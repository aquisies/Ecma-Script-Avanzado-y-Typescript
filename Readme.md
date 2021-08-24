# EcmaScript Avanzado y TypeScript

**Formato**: Un documento con extensión ts con nombre `TS+ApellidoNombre`.

**Sugerencia**: Utilizar Node.js y el compilador TypeScript Compiler (TSC).

## Inicialización de proyecto

Instalando Node.js

```javascript
npm init
```

Al ejecutar la instrucción puedes diligenciar los parametros solicitados o bien en esta ocasión dejar los valores por defecto presionando enter a cada solicitud.

## Instalar compilador TypeScript

```javascript
npm install -D -g typescript
```

Ante problemas de permisos en linux, recuerden ejecutar con privilegios de administrador `sudo`

```javascript
sudo npm install -D -g typescript
```

**Nota:** No olvidar la bandera -g para definir como global la instalación del TypeScript

## Crear el proyecto TypeScript

```javascript
 tsc --init
```

Si todo va bien, crearán el archivo `tsconfig.json` en el modificaré las propiedades a continuación, de acuerdo a su nivel de experiencia modifican las que consideren se ajusta al código que están creando.

```javascript
"compilerOptions":{

"target": "es6",
"lib": [
          "ES2019",
           "DOM",
					],
"outDir": "./build"
}

```

Para este ejercicio editaré las propiedades `target, lib y outDir` como nos lo indica las diapositivas de clase, el outDir albergará los archivos transpilados o compilados.

## Consigna: 

#### Crear dos funciones llamadas operación y operaciones.

**Recuerda la estructura de nombre de archivo:** `TS+TuApellidoTuNombre.ts`

Operación recibirá dos números y un string con el nombre de la operación a efectuar entre ellos: 'suma' ó 'resta' y cargará dinámicamente un módulo para realizar dicho cálculo.

```javascript
const operacion = async (
	// Oportunidad para aplicar async/await
	valor1: number,
	valor2: number,
	nombreOperacion: string
): Promesa<void> => {
	//Oportunidad para aplicar Promesas y  funcion flecha
	try {
		// Según sea nombreOperacion capturar ruta de la clase (Suma o Resta) no se require la extensión en filename
		const { default: typeOperator } = await import(filename); //Oportunidad para aplicar Dynamic import
		const operador: typeof typeOperator = new typeOperator(valor1, valor2); // Oportunidad para aplicar typeof
		return operador.operacion();
	} catch (err) {
		console.error(err);
	}
};

// Operaciones llamará a operacion con los casos de prueba, representando sus salidas.
// operacion deberá devolver el resultado a operaciones a través de una promesa.
const operaciones = () => {
	operacion(5, 7, "suma").then(console.log); // 12
	operacion(10, 2, "resta").then(console.log); // 9
};
operaciones();
```

Los constructores de las clases Suma y Resta recibe dos variables que se asignan a variables privadas

````
Suma.ts
```javascript
Class Suma.ts
	declaracion de varibles privadas
 	constructor( x , y)
	   asignacion de varibles privadas


//Operacion es un metodo que resta x+y

````

Resta.ts

```javascript
Class Resta.ts
	declaracion de varibles privadas
 	constructor( x , y)
	   asignacion de varibles privadas

 Operacion es un metodo que resta x- y

```

**Recursos aplicados:**

- Clases
- Dynamic import (await import)
- Promises
- Async / Await
- Funciones flecha
- Tipado (typeof)

**COMPILANDO**: Por alguna razón la compilación del archivo principal no me funcionó, en clase nos explicarán el porqué.

Por ahora **Compilar** con la siguiente instrucción. Lo cual permitirá generar los archivos ejecutables con Node.js,

```javascript
tsc -p tsconfig.json
```

// Debe ser compilado para generar un archivo javascript ejecutable por Node.js.
