# CPU-Simulator using Windows Forms

This project provides a Windows Forms application that demonstrates common CPU scheduling algorithms through an interactive graphical interface. Process data is entered via a DataGrid, and results are displayed in formatted tables showing waiting times, turnaround times, and other scheduling metrics.

**Fork maintained by Chris Regan** - Original creator: Francis (used with permission)

## Project status

The simulator is functional but still a work in progress. Currently the following scheduling strategies are available:

| Algorithm | Implementation Method | Location |
|-----------|----------------------|----------|
| First Come First Serve (FCFS) | `RunFCFSAlgorithm()` | CpuSchedulerForm.cs:247 |
| Shortest Job First (SJF) | `RunSJFAlgorithm()` | CpuSchedulerForm.cs:283 |
| Priority Scheduling | `RunPriorityAlgorithm()` | CpuSchedulerForm.cs:331 |
| Round Robin (RR) | `RunRoundRobinAlgorithm()` | CpuSchedulerForm.cs:379 |

### Adding Custom Algorithms

Students: You are encouraged to research and implement additional CPU scheduling algorithms beyond those provided. This might include SRTF, MLFQ, HRRN, CFS, EDF, or any other scheduling algorithm you discover in your research.

To add your own scheduling algorithm:

1. Open `CpuSchedulerForm.cs` and find the TODO section around line 1296
2. Create a new method following this pattern:

   ```csharp
   private List<SchedulingResult> RunYourAlgorithm(List<ProcessData> processes)
   {
       var results = new List<SchedulingResult>();
       // Your algorithm implementation here
       return results;
   }
   ```

3. Use `GetProcessDataFromGrid()` to access process data from the UI
4. Add a button click handler that calls your algorithm and displays results using `DisplaySchedulingResults()`
5. Add a button to the UI (see detailed instructions in the TODO comments or main.tex Section 4.4)
6. See existing implementations (FCFS, SJF, Priority, RR) for complete examples

**Detailed instructions** for adding algorithms and buttons can be found in the TODO comments at line 1296 in CpuSchedulerForm.cs.

## Requirements

- Windows operating system
- .NET 8.0 SDK or newer
- Visual Studio 2022 or VS Code with C# extensions

## How to run

### Using Visual Studio

1. Clone the repository:

   ```bash
   git clone git@github.com:iAmGiG/CS-3502-CPU-Sim-Project-StartingPoint.git
   ```

2. Open `CpuScheduler.sln` in Visual Studio 2022
3. Press F5 to build and run the application

### Using VS Code

1. Clone the repository:

   ```bash
   git clone git@github.com:iAmGiG/CS-3502-CPU-Sim-Project-StartingPoint.git
   ```

2. Install the C# Dev Kit extension in VS Code

3. Open the project folder in VS Code

4. **Option A - Using the Debugger (Recommended):**
   - Press **F5** or go to Run & Debug panel
   - Select ".NET Core Launch (console)" configuration
   - This will build and launch the Windows Forms app with debugging support

5. **Option B - Using Terminal (May have termination issues):**

   ```bash
   dotnet build
   dotnet run --project CpuScheduler/CpuScheduler.csproj
   ```

   **Note:** Windows Forms apps may not terminate cleanly in VS Code's integrated terminal

6. **Option C - Run the Built Executable Directly:**

   ```bash
   dotnet build
   # Then navigate to: CpuScheduler/bin/Debug/net8.0-windows/CpuScheduler.exe
   # Double-click the .exe file or run from command prompt
   ```

### Using .NET CLI

From the project root directory:

```bash
# Build the project
dotnet build

# Run the application
dotnet run --project CpuScheduler/CpuScheduler.csproj
```

## Usage

1. Navigate to the **Scheduler** panel using the sidebar
2. Enter the desired number of processes and click "Set Process Count"
3. Edit process data directly in the DataGrid (Burst Time, Priority, Arrival Time)
4. Optionally use "Generate Random" to populate with random values or "Load Example" for preset scenarios
5. Click any algorithm button (FCFS, SJF, Priority, or Round Robin) to run the simulation
6. View detailed results in the **Results** panel including waiting times, turnaround times, and summary statistics

### License

This project is licensed under the terms of the [MIT license](LICENSE.txt).
