1. Open Project Terminal and Run following Commands (your directory should be the one that contains bin folder).
2. Install ElectronNET.API NuGet package in the application:
    dotnet add package ElectronNET.API.
3. Create a local .NET tool manifest file This will create a manifest file.
    dotnet new tool-manifest.
4.Install the electronize tool locally in the project
    dotnet tool install ElectronNET.CLI.
5.Now  configure Electron.NET manifest tool and update the launch profile of the application
    dotnet electronize init
6. Then to integrate Electron.Net in the application I made some changes in the program.cs file Right before "var app = builder.Build();" line.
    builder.Services.AddElectron();
    builder.WebHost.UseElectron(args);

    if (HybridSupport.IsElectronActive)
    {
        // Open the Electron-Window here
        Task.Run(async () => {
            var window = await Electron.WindowManager.CreateWindowAsync();
        });
    }
7. Run The Application 
    dotnet electronize start
