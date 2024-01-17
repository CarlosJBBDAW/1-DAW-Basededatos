sqlite3 tarea3.db 
.read empleados-dump.sql
.mode box
select * from empleados;

| id │  nombre   │ salario │   departamento   │
├────┼───────────┼─────────┼──────────────────┤
│ 1  │ Juan      │ 50000.0 │ Ventas           │
│ 2  │ María     │ 60000.0 │ TI               │
│ 3  │ Carlos    │ 55000.0 │ Ventas           │
│ 4  │ Ana       │ 48000.0 │ Recursos Humanos │
│ 5  │ Pedro     │ 70000.0 │ TI               │
│ 6  │ Laura     │ 52000.0 │ Ventas           │
│ 7  │ Javier    │ 48000.0 │ Recursos Humanos │
│ 8  │ Carmen    │ 65000.0 │ TI               │
│ 9  │ Miguel    │ 51000.0 │ Ventas           │
│ 10 │ Elena     │ 55000.0 │ Recursos Humanos │
│ 11 │ Diego     │ 72000.0 │ TI               │
│ 12 │ Sofía     │ 49000.0 │ Ventas           │
│ 13 │ Andrés    │ 60000.0 │ Recursos Humanos │
│ 14 │ Isabel    │ 53000.0 │ TI               │
│ 15 │ Raúl      │ 68000.0 │ Ventas           │
│ 16 │ Patricia  │ 47000.0 │ Recursos Humanos │
│ 17 │ Alejandro │ 71000.0 │ TI               │
│ 18 │ Natalia   │ 54000.0 │ Ventas           │
│ 19 │ Roberto   │ 49000.0 │ Recursos Humanos │
│ 20 │ Beatriz   │ 63000.0 │ TI               │

1.Muestra el nombre de todos los empleados en mayúsculas.

sqlite> Select upper (nombre) as nombre_mayusculas from empleados;

|nombre_mayusculas  │
├───────────────────┤
│ JUAN              │
│ MARíA             │
│ CARLOS            │
│ ANA               │
│ PEDRO             │
│ LAURA             │
│ JAVIER            │
│ CARMEN            │
│ MIGUEL            │
│ ELENA             │
│ DIEGO             │
│ SOFíA             │
│ ANDRéS            │
│ ISABEL            │
│ RAúL              │
│ PATRICIA          │
│ ALEJANDRO         │
│ NATALIA           │
│ ROBERTO           │
│ BEATRIZ           |

2.Calcula el valor absoluto del salario de todos los empleados.

select nombre, CAST(salario AS INTEGER) AS salario_entero from empleados;

|nombre     │ salario_entero │
├───────────┼────────────────┤
│ Juan      │ 50000          │
│ María     │ 60000          │
│ Carlos    │ 55000          │
│ Ana       │ 48000          │
│ Pedro     │ 70000          │
│ Laura     │ 52000          │
│ Javier    │ 48000          │
│ Carmen    │ 65000          │
│ Miguel    │ 51000          │
│ Elena     │ 55000          │
│ Diego     │ 72000          │
│ Sofía     │ 49000          │
│ Andrés    │ 60000          │
│ Isabel    │ 53000          │
│ Raúl      │ 68000          │
│ Patricia  │ 47000          │
│ Alejandro │ 71000          │
│ Natalia   │ 54000          │
│ Roberto   │ 49000          │
│ Beatriz   │ 63000          |

3.Muestra la fecha actual.

SELECT CURRENT_DATE AS fecha_actual FROM empleados LIMIT 1;
┌──────────────┐
│ fecha_actual │
├──────────────┤
│ 2024-01-17   │
└──────────────┘

4.Calcula el promedio de salarios de todos los empleados.

Select AVG(salario) as salario_promedio from empleados;
┌──────────────────┐
│ salario_promedio │
├──────────────────┤
│ 57000.0          │
└──────────────────┘

5.Convierte la cadena '123' a un valor entero.

select id, CAST(salario AS INTEGER) as salarios from empleados where id between 1 and 3;
┌────┬──────────┐
│ id │ salarios │
├────┼──────────┤
│ 1  │ 50000    │
│ 2  │ 60000    │
│ 3  │ 55000    │
└────┴──────────┘

6.Concatena el nombre y el departamento de cada empleado.

SELECT nombre || ' ' ||  departamento AS nombre_departamento from empleados;
┌───────────────────────────┐
│    nombre_departamento    │
├───────────────────────────┤
│ Juan Ventas               │
│ María TI                  │
│ Carlos Ventas             │
│ Ana Recursos Humanos      │
│ Pedro TI                  │
│ Laura Ventas              │
│ Javier Recursos Humanos   │
│ Carmen TI                 │
│ Miguel Ventas             │
│ Elena Recursos Humanos    │
│ Diego TI                  │
│ Sofía Ventas              │
│ Andrés Recursos Humanos   │
│ Isabel TI                 │
│ Raúl Ventas               │
│ Patricia Recursos Humanos │
│ Alejandro TI              │
│ Natalia Ventas            │
│ Roberto Recursos Humanos  │
│ Beatriz TI                │
└───────────────────────────┘

7.Concatena el nombre y el departamento de cada empleado con un guion como separador.

SELECT nombre || '-' ||  departamento AS nombre_departamento from empleados;
┌───────────────────────────┐
│    nombre_departamento    │
├───────────────────────────┤
│ Juan-Ventas               │
│ María-TI                  │
│ Carlos-Ventas             │
│ Ana-Recursos Humanos      │
│ Pedro-TI                  │
│ Laura-Ventas              │
│ Javier-Recursos Humanos   │
│ Carmen-TI                 │
│ Miguel-Ventas             │
│ Elena-Recursos Humanos    │
│ Diego-TI                  │
│ Sofía-Ventas              │
│ Andrés-Recursos Humanos   │
│ Isabel-TI                 │
│ Raúl-Ventas               │
│ Patricia-Recursos Humanos │
│ Alejandro-TI              │
│ Natalia-Ventas            │
│ Roberto-Recursos Humanos  │
│ Beatriz-TI                │
└───────────────────────────┘

8.Categoriza a los empleados según sus salarios.

select * from empleados order by salario;
┌────┬───────────┬─────────┬──────────────────┐
│ id │  nombre   │ salario │   departamento   │
├────┼───────────┼─────────┼──────────────────┤
│ 16 │ Patricia  │ 47000.0 │ Recursos Humanos │
│ 4  │ Ana       │ 48000.0 │ Recursos Humanos │
│ 7  │ Javier    │ 48000.0 │ Recursos Humanos │
│ 12 │ Sofía     │ 49000.0 │ Ventas           │
│ 19 │ Roberto   │ 49000.0 │ Recursos Humanos │
│ 1  │ Juan      │ 50000.0 │ Ventas           │
│ 9  │ Miguel    │ 51000.0 │ Ventas           │
│ 6  │ Laura     │ 52000.0 │ Ventas           │
│ 14 │ Isabel    │ 53000.0 │ TI               │
│ 18 │ Natalia   │ 54000.0 │ Ventas           │
│ 3  │ Carlos    │ 55000.0 │ Ventas           │
│ 10 │ Elena     │ 55000.0 │ Recursos Humanos │
│ 2  │ María     │ 60000.0 │ TI               │
│ 13 │ Andrés    │ 60000.0 │ Recursos Humanos │
│ 20 │ Beatriz   │ 63000.0 │ TI               │
│ 8  │ Carmen    │ 65000.0 │ TI               │
│ 15 │ Raúl      │ 68000.0 │ Ventas           │
│ 5  │ Pedro     │ 70000.0 │ TI               │
│ 17 │ Alejandro │ 71000.0 │ TI               │
│ 11 │ Diego     │ 72000.0 │ TI               │
└────┴───────────┴─────────┴──────────────────┘

9.Calcula la suma total de salarios de todos los empleados.

Select SUM(salario) as salario_total from empleados;
┌───────────────┐
│ salario_total │
├───────────────┤
│ 1140000.0     │
└───────────────┘

10.Redondea el salario de todos los empleados a dos decimales.

SELECT nombre, ROUND(salario,2) AS salario_redondeado from empleados;
┌───────────┬────────────────────┐
│  nombre   │ salario_redondeado │
├───────────┼────────────────────┤
│ Juan      │ 50000.0            │
│ María     │ 60000.0            │
│ Carlos    │ 55000.0            │
│ Ana       │ 48000.0            │
│ Pedro     │ 70000.0            │
│ Laura     │ 52000.0            │
│ Javier    │ 48000.0            │
│ Carmen    │ 65000.0            │
│ Miguel    │ 51000.0            │
│ Elena     │ 55000.0            │
│ Diego     │ 72000.0            │
│ Sofía     │ 49000.0            │
│ Andrés    │ 60000.0            │
│ Isabel    │ 53000.0            │
│ Raúl      │ 68000.0            │
│ Patricia  │ 47000.0            │
│ Alejandro │ 71000.0            │
│ Natalia   │ 54000.0            │
│ Roberto   │ 49000.0            │
│ Beatriz   │ 63000.0            │
└───────────┴────────────────────┘
select LENGTH(nombre) as longitud_nombre from empleados;
┌─────────────────┐
│ longitud_nombre │
├─────────────────┤
│ 4               │
│ 5               │
│ 6               │
│ 3               │
│ 5               │
│ 5               │
│ 6               │
│ 6               │
│ 6               │
│ 5               │
│ 5               │
│ 5               │
│ 6               │
│ 6               │
│ 4               │
│ 8               │
│ 9               │
│ 7               │
│ 7               │
│ 7               │
└─────────────────┘
Select CURRENT_TIME as tiempo from empleados LIMIT 1;
┌──────────┐
│  tiempo  │
├──────────┤
│ 20:17:22 │
└──────────┘
select salario from empleados;
┌─────────┐
│ salario │
├─────────┤
│ 50000.0 │
│ 60000.0 │
│ 55000.0 │
│ 48000.0 │
│ 70000.0 │
│ 52000.0 │
│ 48000.0 │
│ 65000.0 │
│ 51000.0 │
│ 55000.0 │
│ 72000.0 │
│ 49000.0 │
│ 60000.0 │
│ 53000.0 │
│ 68000.0 │
│ 47000.0 │
│ 71000.0 │
│ 54000.0 │
│ 49000.0 │
│ 63000.0 │
└─────────┘
