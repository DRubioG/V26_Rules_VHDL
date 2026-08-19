# VHDL Reglas

En este documento figuran las buenas prácticas para la programación en VHDL.

# Reglas

## Puertos
Los puertos se definen siempre en mayúsculas con el sufijo dependiendo de si es un puerto de entrada, salida o bidireccional.

``` VHDL
A_I : in std_logic;
B_O : out std_logic_vector(3 downto 0);
C_IO : inout std_logic;
```

## Genéricos
Los genéricos se tienen que definir en mayúsculas con el prefijo 'G_' para indicar que son un genérico.

``` VHDL
G_WIDTH : integer := 8
```


## Señales
Las señales se tienen que definir en minúsculas con el prefijo 's_' para indicar que son una señal.

``` VHDL
signal s_conex : std_logic;
```

## Registros
Los registros se tienen que definir en minúsculas con el prefijo 'r_' para indicar que son un registro.

``` VHDL
signal r_regist : std_logic;
```

## Constantes
Las constantes se tienen que definir en mayúsculas con el prefijo 'C_' para indicar que son una constante.

``` VHDL
constant C_WIDTH : integer := 8
```

## Type
Los type se tienen que definir en minúsculas con el prefijo 't_' para indicar que son un type.

``` VHDL
type t_mem is array (0 to 100) of std_logic_vector(G_WIDTH-1 downto 0);
```

## Máquinas de estados
Las máquinas de estados se tienen que definir indicando que son diferentes de otro tipo.
- El type de las máquinas de estados tiene que incluir el nombre 'fsm' para saber que es una máquina de estados.
- Los estados se definen en mayúsculas con el prefijo 'SM_'.
- Y el registro que lleva la máquina de estados tiene que llevar el prefijo 're_'.

``` VHDL
type fsm is (
    SM_IDLE,
    SM_START,
    SM_FINISH
);
signal re_state : fsm;
```

## process
Los process tienen que llevar el nombre especifico de lo que hacen en la definición.

``` VHDL
COUNTER_PROCESS : process(clk)
begin
    ...
end process;
```

## Funciones
Las funciones se tienen que definir con el prefijo 'f_' para indicar que son funciones.

``` VHDL
function f_counter (TEST_I : in std_logic) return std_logic is
    begin
    ...
end function;
```

## Procedures
Los procedures se tienen que definir con el prefijo 'p_' para indicar que son procedures.

``` VHDL
procedure p_counter(TEST_I : in std_logic; 
                    TEST_O : out std_logic_vector(15 downto 0) is
    begin
    ...
end procedure;
```

## Variables
Las variables se tienen que definir en minúsculas con el prefijo 'v_' para indicar que son variables.

``` VHDL
process(CLK_I)
    variable v_cont : integer range 0 to 15;
begin
    ...
end process;
```

## Package
### Nombre del package
El nombre de los package tiene que empezar por el prefijo 'pk_'.

### Valores de un package
Los valores de un package tiene que llevar el prefijo 'pk_' o 'PK_' si es una constante.


``` VHDL
package pk_test is
    constant PK_VALUE : integer := 8;

function pk_f_counter (TEST_I : in std_logic) return std_logic;

end package;

package body pk_test is

function pk_f_counter (TEST_I : in std_logic) return std_logic is
    begin
...
end function;

end package body;
```
