# Generar número aleatorio
 Descripción: Anteriormente el número aleatorio estaba generado entre 0 y 10. Se cambió a 1 y 100
 
 Se utiliza la función floor, para redondear el número al próximo número entero 


 let randomNumber = Math.random() * 10;

 ahora

 let randomNumber = Math.floor(Math.random() * 100) + 1;

 ## Corrección cantidad de intentos

 Descripción: El número de intentos estaba en 5, lo cual no era lo correcto. Se cambió a 10

 Antes

 const ATTEMPS = 5;

 Ahora

 const ATTEMPS = 10;

 ## Selector incorrecto loWOrHi

 Descripción: Al momento de seleccionar por clases, se necesita colocar "." antes de lowOrHi.

 Antes

 const lowOrHi = document.querySelector('lowOrHi');

 Ahora

 const lowOrHi = document.querySelector('.lowOrHi');

 ## Sintaxis inadecuado en addEventListener()

 Descripción: addeventListener debe de escribirse con "E" mayúscula. Así. addEventListener(); Corregír con los addEventListener usados.

 Antes

 guessSubmit.addeventListener('click', checkGuess);

 Ahora

 guessSubmit.addEventListener('click', checkGuess);

 ## Mensajes de alerta

 Descripción: Los mensajes que se muestran al usuario están en posiciones que no deben. según las especificaciones mencionadas. Se corrigieron según el los ejemplos de abajo.

Antes 

    if(userGuess === randomNumber) {
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'black';
      lowOrHi.textContent = '';
      setGameOver();
    } else if(guessCount === ATTEMPS) {
      lastResult.textContent = 'Felicitaciones! adivinaste el número!';
      lastResult.style.backgroundColor = 'red';
      setGameOver();
    } else {
      lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'green';
      if(userGuess < randomNumber) {
        lowOrHi.textContent = 'El número es mayor!';
      } else if(userGuess > randomNumber) {
        lowOrHi.textContent = 'El número es menor!';
      }
    }

Ahora

    if(userGuess === randomNumber) {
      lastResult.textContent = 'Felicitaciones! adivinaste el número!';
      lastResult.style.backgroundColor = 'green';
      lowOrHi.textContent = '';
      setGameOver();
    } else if(guessCount === ATTEMPS) {
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'red';
      lowOrHi.textContent = '';
      setGameOver();
    } else {
      lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'black';
      if(userGuess < randomNumber) {
        lowOrHi.textContent = 'El número es mayor!';
      } else {
        lowOrHi.textContent = 'El número es menor!';
      }
    }

 ## Validaciones de números ingresados

 Descripción:

 - No se valida si el número ingresado es entero
 - Rango de 1 - 100 no verificado
 - Los intentos se incrementa aún cuando el usuario ingresa un valor incorrecto

Antes

    let userGuess = guessField.value;

Ahora

    let userGuess = Number(guessField.value);

    if(!Number.isInteger(userGuess) || userGuess < 1 || userGuess > 100) {
        alert('Ingresa un número entero entre 1 y 100.');
        guessField.value = '';
        guessField.focus();
        return;
      }

 ## Generación incorrecta del número aleatorio resetGame

 Descripción: El código que estaba, generaba el número 1 siempre. Se usa la lógica anterior para corregir este error.

 Antes 

    randomNumber = Math.floor(Math.random()) + 1;

Ahora

    randomNumber = Math.floor(Math.random() * 100) + 1;

