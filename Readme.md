## 📦 Installation Guide

- Install [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.1) 3.1.300 or later

- Create Blazor WebAssembly Project

  ```bash
  $ dotnet new blazorwasm -o MyAntDesignApp
  ```

- Go to the project folder of the application and install the Nuget package reference

  ```bash
  $ cd MyAntDesignApp
  $ dotnet add package AntDesign --version 0.1.0-*
  ```

- Register the services

  ```csharp
  services.AddAntDesign();
  ```

- Link the static files in `wwwroot/index.html` (WebAssembly) or `Pages/_Host.razor` (Server)

  ```html
  <link href="_content/AntDesign/css/ant-design-blazor.css" rel="stylesheet" />
  <script src="_content/AntDesign/js/ant-design-blazor.js"></script>
  ```

- Add namespace in `_Imports.razor`

  ```csharp
  @using AntDesign
  ```

- To display the pop-up component dynamically, you need to add the `<AntContainer />` component in `App.razor`. 

  ```
  <Router AppAssembly="@typeof(MainLayout).Assembly">
      <Found Context="routeData">
          <RouteView RouteData="routeData" DefaultLayout="@typeof(MainLayout)" />
      </Found>
      <NotFound>
          <LayoutView Layout="@typeof(MainLayout)">
              <Result Status="404" />
          </LayoutView>
      </NotFound>
  </Router>

  <AntContainer />   <-- add this component ✨
  ```

- Finally, it can be referenced in the `.razor' component!

  ```html
  <Button Type="primary">Hello World!</Button>
  ```
