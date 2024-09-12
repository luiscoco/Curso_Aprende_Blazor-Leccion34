# CURSO: APRENDE BLAZOR

# LECCIÓN 34: Sección NotFound en el componente Router y error 404 (Not Found)

1. Abrir la aplicación con Visual Studio 2022 o VSCode

2. **Ejemplo 1**: 

```razor
<Router AppAssembly="@typeof(App).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
        <FocusOnNavigate RouteData="@routeData" Selector="h1" />
    </Found>
    <NotFound>
        <PageTitle>Not found</PageTitle>
        <LayoutView Layout="@typeof(MainLayout)">
            <p role="alert">Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

3. **Ejemplo 2**: Primero creamos el componente NotFound.razor:

NotFound.razor (for displaying the 404 error)

```razor
@page "/notfound"

<h3>Page Not Found</h3>
<p>Sorry, but the page you are looking for does not exist.</p>
<p><a href="/">Go back to Home</a></p>
```

Después invocamos dicho componente desde App.razor cuando el Componente Router no encuentra la ruta de un componente que corresponda a la ruta que hemos introducido en el buscador de internet o hayamos referenciado en el componente NavMenu.razor 

```razor
<Router AppAssembly="@typeof(App).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <NotFound />
        </LayoutView>
    </NotFound>
</Router>
```

3. **Ejemplo 3**: error not found 404. Ver referencias: 

https://github.com/dotnet/aspnetcore/issues/52660

https://stackoverflow.com/questions/78859123/notfound-route-not-working-in-blazor-even-in-newly-created-project

```csharp
app.UseStatusCodePagesWithRedirects("/404");
app.Run();
Add a _404.razor page to your Pages folder.
```

```razor
@page "/404"
<h3>Show me 404</h3>
@code {
    
}
```
