# PLSQL
En este repositorio, organizare todo lo que tenga que ver con plsql  ejemplos y demas

create or replace PACKAGE paqueteTrabajador AS 
  /*Se declaran los metodos y atributos Similar a INTERFAZ EN JAVA */ 
PROCEDURE ALGO(valor1 varchar2, valor2 varchar2);
PROCEDURE actualizarAlgo (idbuscar varchar2, id2Modificado varchar2);
PROCEDURE borrarAlgo (idbuscar varchar2);
PROCEDURE listarAlgo;
PROCEDURE listarAlgoPorID(idbuscar varchar2);
END paqueteTrabajador;
/

create or replace PACKAGE BODY paqueteTrabajador AS 
/*Ejemplo INSERT INTO*/
PROCEDURE ALGO(valor1 varchar2, valor2 varchar2) AS
resultado varchar2(10);
  BEGIN
    INSERT INTO ALGO(id,id2)
    VALUES(valor1,valor2);
    resultado:= 'Exito';
  END ALGO;
  /*Ejemplo UPDATE*/
PROCEDURE actualizarAlgo (idbuscar varchar2, id2Modificado varchar2) IS     
   BEGIN            
         UPDATE algo SET id2 = id2Modificado WHERE id = idbuscar;
   END actualizarAlgo;

/*Ejemplo UPDATE*/
PROCEDURE borrarAlgo (idbuscar varchar2) IS     
   BEGIN            
         Delete From algo WHERE id = idbuscar;
   END borrarAlgo;

/*Ejemplo listar Todo*/
PROCEDURE listarAlgo IS
CURSOR cur IS SELECT * FROM algo;
fila cur%ROWTYPE;
BEGIN
    OPEN cur;
        LOOP
            FETCH CUR INTO fila;
            EXIT WHEN CUR%NOTFOUND;
            DBMS_OUTPUT.put_liNE(fila.id || ' ' ||fila.id2);
        END LOOP;
    CLOSE cur;
END listarAlgo;

/*Ejemplo Listar Por ID*/
PROCEDURE listarAlgoPorID(idbuscar varchar2) IS
CURSOR cur IS SELECT * FROM algo Where id =idbuscar;
fila cur%ROWTYPE;
BEGIN
    OPEN cur;
        LOOP
            FETCH CUR INTO fila;
            EXIT WHEN CUR%NOTFOUND;
            DBMS_OUTPUT.put_liNE(fila.id || ' ' ||fila.id2);
        END LOOP;
    CLOSE cur;
END listarAlgoPorID;

END paqueteTrabajador;
/
