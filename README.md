# 1. Investiga la llibreria System.Diagnostics. Enumera i explica els mètodes i propietats més rellevants o útils que trobis.
1. Classe Debug
Per registrar informació quan estàs desenvolupant (només en mode debug).
Ex: Debug.Write(string): Escriu un missatge a la consola de depuració.
2. Classe Trace
Similar a Debug, però funciona en qualsevol mode (Debug o Release).
Ex: Trace.Write(string): Escriu una línia de registre.
3. Classe Process
Per executar i controlar processos del sistema operatiu.
Ex: Process.Start(string fileName): Inicia un fitxer o aplicació (per exemple, un .exe).
4. Classe EventLog
Treballa amb el registre d'esdeveniments de Windows.
Ex: EventLog.WriteEntry(string source, string message): Escriu un missatge a l'esdeveniment.
5. Classe PerformanceCounter
Accedeix a contadors de rendiment (CPU, memòria, etc.).
Ex: PerformanceCounter.NextValue(): Llegeix el valor actual del contador.

# 2. Realitza un programa que imprimeixi per pantalla tots el nom i el PID (Process ID) que estan en execució de la màquina que estàs fent servir. Guarda aquesta llista en un arxiu de text.
A l'enllaç al final del readme

# 3. Executa un programa browser (Edge, Chrome, Firefox). Fent servir la classe ProcessThread i amb del programa anterior crea un mètode que llista els fils que té el browser i imprimeix el seu ID, hora d’inici i prioritat. Si obres més d’una pestanya, s’obren nous fils? Explica que succeix.
Si, s'obren nous fils. Crea un nou procés o nous fils dins del procés principal.

# 4. Investiga la classe Thread. Quins mètodes en destacaries? Fes un quadre comparatiu amb Task.
1.- Thread 
Start()	Inicia l'execució del fil.	Necessari després de crear-lo.
Join()	Bloqueja el fil actual fins que el fil en qüestió acabi.	Molt útil per sincronitzar.
Sleep(int milliseconds)	Pausa el fil actual durant un temps.	Fa sleep sense consumir CPU.
IsAlive (propietat)	Indica si el fil encara està actiu.	Només lectura.
Priority (propietat)	Permet canviar la prioritat del fil (valor: ThreadPriority).	Control del sistema operatiu.
Name (propietat)	Assigna un nom per identificar el fil.	Opcional però útil per debugging.

2.- Comparació
| Característica        | Thread                                       | Task                                                   |
|------------------------|----------------------------------------------|--------------------------------------------------------|
| Concepte               | Fil manual, baix nivell                     | Treball asíncron d'alt nivell (gestiona fils internament) |
| Creació                | `new Thread(() => { })`                     | `Task.Run(() => { })` o `async/await`                  |
| Inici                  | `Start()` manual                            | Automàtic en `Run` o `Start`                           |
| Gestió de recursos     | Manual (pots consumir més fils)             | Gestió automàtica via `ThreadPool`                     |
| Sincronització         | `Join()`, `Lock`, `Monitor`                 | `await`, `WhenAll`, `WhenAny`                          |
| Cancel·lació           | Complicada (no nativa)                      | Fàcil amb `CancellationToken`                         |
| Escalabilitat          | Baixa (un fil per operació)                 | Alta (comparteix fils, molt més eficient)              |
| Ús típic               | Control total sobre fils, operacions pesades| Operacions asíncrones, treball paral·lel lleuger       |
| Exemple                | `Thread t = new Thread(MyMethod); t.Start();`| `await Task.Run(() => MyMethod());`                    |

# 5. Crea un programa amb 5 fils que escriuen per consola: $“Hola! Soc el fil número {numeroFil}”
Executa els 5 fils  i comprova l’ordre que s’imprimeix. Quin és? i per què es aquest ordre?
Random. Perque els processos competeixen per el temps de la CPU.
Fes servir la funció .Sleep() per mirar de fer que les tasques s’executin en ordre invers.

# 6. Carrera de camells!
Realitza un programa que emuli una carrera de camells. Cada camell és un thread diferent. Els camells han de comptar de 0 a 100. A cada comptatge escriu per consola el número de camell i el número pel qual va, a més a més descansarà X milisegons. X serà un número aleatori  a cada cicle d’entre dos valors. Els dos valors són paràmetres diferents entre els camells.

[Enllaç al github amb el codi dels exercicis](https://github.com/AlejandroMarEst/T2.Processos)
