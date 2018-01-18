<span data-ttu-id="393f5-101">Sostituire il contenuto del file di vista Razor *Views/HelloWorld/Index.cshtml* con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="393f5-101">Replace the contents of the *Views/HelloWorld/Index.cshtml* Razor view file with the following:</span></span>

[!code-HTML[Main](../../tutorials/first-mvc-app/start-mvc/sample/MvcMovie/Views/HelloWorld/Index.cshtml)]

<span data-ttu-id="393f5-102">Passare a `http://localhost:xxxx/HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="393f5-102">Navigate to `http://localhost:xxxx/HelloWorld`.</span></span> <span data-ttu-id="393f5-103">Il metodo `Index` in `HelloWorldController` non ha eseguito molte operazioni; ha eseguito l'istruzione `return View();` che ha specificato che il metodo deve usare un file di modello della vista per eseguire il rendering di una risposta al browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-103">The `Index` method in the `HelloWorldController` didn't do much; it ran the statement `return View();`, which specified that the method should use a view template file to render a response to the browser.</span></span> <span data-ttu-id="393f5-104">Poiché non è stato specificato in modo esplicito il nome del file di modello della vista, MVC imposta come predefinito il file della vista *Index.cshtml* nella cartella */Views/HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="393f5-104">Because you didn't explicitly specify the name of the view template file, MVC defaulted to using the *Index.cshtml* view file in the */Views/HelloWorld* folder.</span></span> <span data-ttu-id="393f5-105">L'immagine seguente mostra la stringa "Hello from our View Template!"</span><span class="sxs-lookup"><span data-stu-id="393f5-105">The image below shows the string "Hello from our View Template!"</span></span> <span data-ttu-id="393f5-106">hardcoded nella vista.</span><span class="sxs-lookup"><span data-stu-id="393f5-106">hard-coded in the view.</span></span>

![Finestra del browser](../../tutorials/first-mvc-app/adding-view/_static/hell_template.png)

<span data-ttu-id="393f5-108">Se la finestra del browser è di piccole dimensioni, ad esempio in un dispositivo mobile, potrebbe essere necessario alternare (toccare) il [pulsante di spostamento Bootstrap](http://getbootstrap.com/components/#navbar) in alto a destra per rendere visibili i collegamenti **Home**, **About** (Informazioni su) e **Contact** (Contatto).</span><span class="sxs-lookup"><span data-stu-id="393f5-108">If your browser window is small (for example on a mobile device), you might need to toggle (tap) the [Bootstrap navigation button](http://getbootstrap.com/components/#navbar) in the upper right to see the **Home**, **About**, and **Contact** links.</span></span>

![Finestra del browser con il pulsante di navigazione Bootstrap evidenziato](../../tutorials/first-mvc-app/adding-view/_static/1.png)

## <a name="changing-views-and-layout-pages"></a><span data-ttu-id="393f5-110">Modifica delle viste e delle pagine di layout</span><span class="sxs-lookup"><span data-stu-id="393f5-110">Changing views and layout pages</span></span>

<span data-ttu-id="393f5-111">Toccare i collegamenti di menu: **MvcMovie**, **Home** e **About** (Informazioni su).</span><span class="sxs-lookup"><span data-stu-id="393f5-111">Tap the menu links (**MvcMovie**, **Home**, **About**).</span></span> <span data-ttu-id="393f5-112">Ogni pagina mostra lo stesso layout di menu.</span><span class="sxs-lookup"><span data-stu-id="393f5-112">Each page shows the same menu layout.</span></span> <span data-ttu-id="393f5-113">Il layout di menu viene implementato nel file *Views/Shared/_Layout.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="393f5-113">The menu layout is implemented in the *Views/Shared/_Layout.cshtml* file.</span></span> <span data-ttu-id="393f5-114">Aprire il file *Views/Shared/_Layout.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="393f5-114">Open the *Views/Shared/_Layout.cshtml* file.</span></span>

<span data-ttu-id="393f5-115">I modelli di [layout](xref:mvc/views/layout) consentono di specificare il layout del contenitore HTML del sito in un'unica posizione e quindi di applicarlo in più pagine del sito.</span><span class="sxs-lookup"><span data-stu-id="393f5-115">[Layout](xref:mvc/views/layout) templates allow you to specify the HTML container layout of your site in one place and then apply it across multiple pages in your site.</span></span> <span data-ttu-id="393f5-116">Trovare la riga `@RenderBody()`.</span><span class="sxs-lookup"><span data-stu-id="393f5-116">Find the `@RenderBody()` line.</span></span> <span data-ttu-id="393f5-117">`RenderBody` è un segnaposto dove tutte le pagine specifiche della vista vengono presentate, *incapsulate* nella pagina di layout.</span><span class="sxs-lookup"><span data-stu-id="393f5-117">`RenderBody` is a placeholder where all the view-specific pages you create show up, *wrapped* in the layout page.</span></span> <span data-ttu-id="393f5-118">Ad esempio, se si seleziona il collegamento **About** (Informazioni su), il rendering della vista **Views/Home/About.cshtml** viene eseguito all'interno del metodo `RenderBody`.</span><span class="sxs-lookup"><span data-stu-id="393f5-118">For example, if you select the **About** link, the **Views/Home/About.cshtml** view is rendered inside the `RenderBody` method.</span></span>

## <a name="change-the-title-and-menu-link-in-the-layout-file"></a><span data-ttu-id="393f5-119">Modificare il titolo e il collegamento di menu nel file di layout</span><span class="sxs-lookup"><span data-stu-id="393f5-119">Change the title and menu link in the layout file</span></span>

<span data-ttu-id="393f5-120">Nell'elemento del titolo cambiare `MvcMovie` in `Movie App`.</span><span class="sxs-lookup"><span data-stu-id="393f5-120">In the title element, change `MvcMovie` to `Movie App`.</span></span> <span data-ttu-id="393f5-121">Modificare il testo di ancoraggio nel modello di layout da `MvcMovie` a `Mvc Movie` e il controller da `Home` a `Movies`, come evidenziato di seguito:</span><span class="sxs-lookup"><span data-stu-id="393f5-121">Change the anchor text in the layout template from `MvcMovie` to `Mvc Movie` and the controller from `Home` to `Movies` as highlighted below:</span></span>

<span data-ttu-id="393f5-122">Nota: la versione di ASP.NET 2.0 Core è leggermente diversa.</span><span class="sxs-lookup"><span data-stu-id="393f5-122">Note: The ASP.NET Core 2.0 version is slightly different.</span></span> <span data-ttu-id="393f5-123">Non contiene `@inject ApplicationInsights` e `@Html.Raw(JavaScriptSnippet.FullScript)`.</span><span class="sxs-lookup"><span data-stu-id="393f5-123">It doesn't contain `@inject ApplicationInsights` and `@Html.Raw(JavaScriptSnippet.FullScript)`.</span></span>

[!code-html[Main](../../tutorials/first-mvc-app/start-mvc/sample/MvcMovie/Views/Shared/_Layout.cshtml?highlight=7,31)]

>[!WARNING]
> <span data-ttu-id="393f5-124">Il controller `Movies` non è stato ancora implementato e quindi, se si fa clic su questo collegamento, verrà visualizzato un errore 404 (Non trovato).</span><span class="sxs-lookup"><span data-stu-id="393f5-124">We haven't implemented the `Movies` controller yet, so if you click on that link, you'll get a 404 (Not found) error.</span></span>

<span data-ttu-id="393f5-125">Salvare le modifiche e toccare il collegamento **About** (Informazioni su).</span><span class="sxs-lookup"><span data-stu-id="393f5-125">Save your changes and tap the **About** link.</span></span> <span data-ttu-id="393f5-126">Si noti come il titolo sulla scheda del browser visualizzi ora **About - Movie App** (Informazioni su - Movie App) anziché **About - Mvc Movie** (Informazioni su - Mvc Movie):</span><span class="sxs-lookup"><span data-stu-id="393f5-126">Notice how the title on the browser tab now displays **About - Movie App** instead of **About - Mvc Movie**:</span></span> 

![Informazioni sulla scheda](../../tutorials/first-mvc-app/adding-view/_static/about2.png)

<span data-ttu-id="393f5-128">Toccare il collegamento **Contact** e notare che anche il titolo e il testo di ancoraggio visualizzano **Movie App**.</span><span class="sxs-lookup"><span data-stu-id="393f5-128">Tap the **Contact** link and notice that the title and anchor text also display **Movie App**.</span></span> <span data-ttu-id="393f5-129">La modifica è stata apportata una volta nel modello di layout e tutte le pagine nel sito riflettono il nuovo testo del collegamento e il nuovo titolo.</span><span class="sxs-lookup"><span data-stu-id="393f5-129">We were able to make the change once in the layout template and have all pages on the site reflect the new link text and new title.</span></span>

<span data-ttu-id="393f5-130">Esaminare il file *Views/_ViewStart.cshtml*:</span><span class="sxs-lookup"><span data-stu-id="393f5-130">Examine the *Views/_ViewStart.cshtml* file:</span></span>


```HTML
@{
    Layout = "_Layout";
}
```

<span data-ttu-id="393f5-131">Il file *Views/_ViewStart.cshtml* attiva il file *Views/Shared/_Layout.cshtml* per ogni vista.</span><span class="sxs-lookup"><span data-stu-id="393f5-131">The *Views/_ViewStart.cshtml* file brings in the *Views/Shared/_Layout.cshtml* file to each view.</span></span> <span data-ttu-id="393f5-132">È possibile usare la proprietà `Layout` per impostare una vista di layout differente oppure impostarlo su `null` e quindi non verrà usato alcun file di layout.</span><span class="sxs-lookup"><span data-stu-id="393f5-132">You can use the `Layout` property to set a different layout view, or set it to `null` so no layout file will be used.</span></span>

<span data-ttu-id="393f5-133">Cambiare il titolo della vista `Index`.</span><span class="sxs-lookup"><span data-stu-id="393f5-133">Change the title of the `Index` view.</span></span>

<span data-ttu-id="393f5-134">Aprire *Views/HelloWorld/Index.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="393f5-134">Open *Views/HelloWorld/Index.cshtml*.</span></span> <span data-ttu-id="393f5-135">Apportare una modifica in due punti:</span><span class="sxs-lookup"><span data-stu-id="393f5-135">There are two places to make a change:</span></span>

   * <span data-ttu-id="393f5-136">Il testo visualizzato nel titolo del browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-136">The text that appears in the title of the browser.</span></span>
   * <span data-ttu-id="393f5-137">L'intestazione secondaria (elemento `<h2>`).</span><span class="sxs-lookup"><span data-stu-id="393f5-137">The secondary header (`<h2>` element).</span></span>

<span data-ttu-id="393f5-138">Renderli leggermente diversi in modo da poter esaminare la parte specifica di app modificata dal frammento specifico di codice.</span><span class="sxs-lookup"><span data-stu-id="393f5-138">You'll make them slightly different so you can see which bit of code changes which part of the app.</span></span>


```HTML
@{
    ViewData["Title"] = "Movie List";
}

<h2>My Movie List</h2>

<p>Hello from our View Template!</p>
```

<span data-ttu-id="393f5-139">`ViewData["Title"] = "Movie List";` nel codice precedente imposta la proprietà `Title` del dizionario `ViewData` su "Movie List".</span><span class="sxs-lookup"><span data-stu-id="393f5-139">`ViewData["Title"] = "Movie List";` in the code above sets the `Title` property of the `ViewData` dictionary to "Movie List".</span></span> <span data-ttu-id="393f5-140">La proprietà `Title` viene usata nell'elemento HTML `<title>` nella pagina di layout:</span><span class="sxs-lookup"><span data-stu-id="393f5-140">The `Title` property is used in the `<title>` HTML element in the layout page:</span></span>


```HTML
<title>@ViewData["Title"] - Movie App</title>
   ```

<span data-ttu-id="393f5-141">Salvare le modifiche e passare a `http://localhost:xxxx/HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="393f5-141">Save your change and navigate to `http://localhost:xxxx/HelloWorld`.</span></span> <span data-ttu-id="393f5-142">Si noti che il titolo del browser, l'intestazione primaria e le intestazioni secondarie sono cambiati.</span><span class="sxs-lookup"><span data-stu-id="393f5-142">Notice that the browser title, the primary heading, and the secondary headings have changed.</span></span> <span data-ttu-id="393f5-143">Se le modifiche non sono visibili nel browser, è possibile che si stia visualizzando il contenuto memorizzato nella cache.</span><span class="sxs-lookup"><span data-stu-id="393f5-143">(If you don't see changes in the browser, you might be viewing cached content.</span></span> <span data-ttu-id="393f5-144">Premere CTRL + F5 nel browser per forzare il caricamento della risposta dal server. Il titolo del browser viene creato con il valore `ViewData["Title"]` impostato nel modello di vista *Index.cshtml* e la stringa "- Movie App" aggiuntiva viene aggiunta nel file di layout.</span><span class="sxs-lookup"><span data-stu-id="393f5-144">Press Ctrl+F5 in your browser to force the response from the server to be loaded.) The browser title is created with `ViewData["Title"]` we set in the *Index.cshtml* view template and the additional "- Movie App" added in the layout file.</span></span>

<span data-ttu-id="393f5-145">Si noti anche come il contenuto del modello di vista *Index.cshtml* sia stato unito con il modello di vista *Views/Shared/_Layout.cshtml* e sia stata inviata una singola risposta HTML al browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-145">Also notice how the content in the *Index.cshtml* view template was merged with the *Views/Shared/_Layout.cshtml* view template and a single HTML response was sent to the browser.</span></span> <span data-ttu-id="393f5-146">I modelli di layout rendono molto semplice apportare modifiche che si applicano a tutte le pagine dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="393f5-146">Layout templates make it really easy to make changes that apply across all of the pages in your application.</span></span> <span data-ttu-id="393f5-147">Per altre informazioni, vedere [Layout](../../mvc/views/layout.md).</span><span class="sxs-lookup"><span data-stu-id="393f5-147">To learn more see [Layout](../../mvc/views/layout.md).</span></span>

![Vista dell'elenco di film](../../tutorials/first-mvc-app/adding-view/_static/hell3.png)

<span data-ttu-id="393f5-149">Il breve testo di "dati", in questo caso il messaggio "Hello from our View Template!",</span><span class="sxs-lookup"><span data-stu-id="393f5-149">Our little bit of "data" (in this case the "Hello from our View Template!"</span></span> <span data-ttu-id="393f5-150">è tuttavia hardcoded.</span><span class="sxs-lookup"><span data-stu-id="393f5-150">message) is hard-coded, though.</span></span> <span data-ttu-id="393f5-151">L'applicazione MVC ha un elemento "V" (vista) ed è stato ottenuto un elemento "C" (controller), ma non ancora un elemento "M" (modello).</span><span class="sxs-lookup"><span data-stu-id="393f5-151">The MVC application has a "V" (view) and you've got a "C" (controller), but no "M" (model) yet.</span></span>

## <a name="passing-data-from-the-controller-to-the-view"></a><span data-ttu-id="393f5-152">Passaggio di dati dal controller alla vista</span><span class="sxs-lookup"><span data-stu-id="393f5-152">Passing Data from the Controller to the View</span></span>

<span data-ttu-id="393f5-153">Le azioni del controller vengono richiamate in risposta a una richiesta URL in ingresso.</span><span class="sxs-lookup"><span data-stu-id="393f5-153">Controller actions are invoked in response to an incoming URL request.</span></span> <span data-ttu-id="393f5-154">Una classe controller è il punto in cui viene scritto il codice che gestisce le richieste in ingresso del browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-154">A controller class is where you write the code that handles the incoming browser requests.</span></span> <span data-ttu-id="393f5-155">Il controller recupera i dati da un'origine dati e determina il tipo di risposta da inviare al browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-155">The controller retrieves data from a data source and decides what type of response to send back to the browser.</span></span> <span data-ttu-id="393f5-156">I modelli di vista possono essere usati da un controller per generare e formattare una risposta HTML al browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-156">View templates can be used from a controller to generate and format an HTML response to the browser.</span></span>

<span data-ttu-id="393f5-157">Il compito dei controller è fornire i dati necessari affinché un modello di vista possa eseguire il rendering di una risposta.</span><span class="sxs-lookup"><span data-stu-id="393f5-157">Controllers are responsible for providing the data required in order for a view template to render a response.</span></span> <span data-ttu-id="393f5-158">Procedura consigliata: i modelli di vista **non** devono eseguire la logica di business o interagire direttamente con un database.</span><span class="sxs-lookup"><span data-stu-id="393f5-158">A best practice: View templates should **not** perform business logic or interact with a database directly.</span></span> <span data-ttu-id="393f5-159">Un modello di vista deve invece usare solo i dati forniti dal controller.</span><span class="sxs-lookup"><span data-stu-id="393f5-159">Rather, a view template should work only with the data that's provided to it by the controller.</span></span> <span data-ttu-id="393f5-160">Questa "separazione delle problematiche" consente di mantenere il codice pulito e semplifica la gestione e i test.</span><span class="sxs-lookup"><span data-stu-id="393f5-160">Maintaining this "separation of concerns" helps keep your code clean, testable, and maintainable.</span></span>

<span data-ttu-id="393f5-161">Attualmente il metodo `Welcome` nella classe `HelloWorldController` accetta un parametro `name` e `ID` e quindi genera i valori direttamente al browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-161">Currently, the `Welcome` method in the `HelloWorldController` class takes a `name` and a `ID` parameter and then outputs the values directly to the browser.</span></span> <span data-ttu-id="393f5-162">Invece di ottenere il rendering di questa risposta come stringa, cambiare il controller in modo che usi un modello di vista.</span><span class="sxs-lookup"><span data-stu-id="393f5-162">Rather than have the controller render this response as a string, let’s change the controller to use a view template instead.</span></span> <span data-ttu-id="393f5-163">Il modello di vista genererà una risposta dinamica, il che significa che è necessario passare i bit di dati appropriati dal controller alla vista per generare la risposta.</span><span class="sxs-lookup"><span data-stu-id="393f5-163">The view template will generate a dynamic response, which means that you need to pass appropriate bits of data from the controller to the view in order to generate the response.</span></span> <span data-ttu-id="393f5-164">È possibile ottenere questo risultato facendo in modo che il controller inserisca i dati dinamici (parametri) di cui il modello di vista necessita in un dizionario `ViewData` a cui il modello di vista può accedere.</span><span class="sxs-lookup"><span data-stu-id="393f5-164">You can do this by having the controller put the dynamic data (parameters) that the view template needs in a `ViewData` dictionary that the view template can then access.</span></span>

<span data-ttu-id="393f5-165">Tornare al file *HelloWorldController.cs* e modificare il metodo `Welcome` in modo da aggiungere un valore `Message` e `NumTimes` al dizionario `ViewData`.</span><span class="sxs-lookup"><span data-stu-id="393f5-165">Return to the *HelloWorldController.cs* file and change the `Welcome` method to add a `Message` and `NumTimes` value to the `ViewData` dictionary.</span></span> <span data-ttu-id="393f5-166">Il dizionario `ViewData` è un oggetto dinamico, ovvero è possibile inserirvi gli elementi desiderati; l'oggetto `ViewData` non dispone di proprietà definite fino a quando non si inserisce un elemento al suo interno.</span><span class="sxs-lookup"><span data-stu-id="393f5-166">The `ViewData` dictionary is a dynamic object, which means you can put whatever you want in to it; the `ViewData` object has no defined properties until you put something inside it.</span></span> <span data-ttu-id="393f5-167">Il sistema di [associazione di modelli MVC](xref:mvc/models/model-binding) esegue il mapping dei parametri denominati (`name` e `numTimes`) dalla stringa di query nella barra degli indirizzi ai parametri nel metodo.</span><span class="sxs-lookup"><span data-stu-id="393f5-167">The [MVC model binding system](xref:mvc/models/model-binding) automatically maps the named parameters (`name` and `numTimes`) from the query string in the address bar to parameters in your method.</span></span> <span data-ttu-id="393f5-168">Il file *HelloWorldController.cs* completo avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="393f5-168">The complete *HelloWorldController.cs* file looks like this:</span></span>

[!code-csharp[Main](../../tutorials/first-mvc-app/start-mvc/sample/MvcMovie/Controllers/HelloWorldController.cs?name=snippet_5)]

<span data-ttu-id="393f5-169">L'oggetto di dizionario `ViewData` contiene i dati che verranno passati alla vista.</span><span class="sxs-lookup"><span data-stu-id="393f5-169">The `ViewData` dictionary object contains data that will be passed to the view.</span></span> 

<span data-ttu-id="393f5-170">Creare un modello di vista Welcome denominato *Views/HelloWorld/Welcome.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="393f5-170">Create a Welcome view template named *Views/HelloWorld/Welcome.cshtml*.</span></span>

<span data-ttu-id="393f5-171">Si creerà un ciclo nel modello di vista *Welcome.cshtml* che visualizza la stringa "Hello" `NumTimes`.</span><span class="sxs-lookup"><span data-stu-id="393f5-171">You'll create a loop in the *Welcome.cshtml* view template that displays "Hello" `NumTimes`.</span></span> <span data-ttu-id="393f5-172">Sostituire il contenuto di *Views/HelloWorld/Welcome.cshtml* con quanto segue:</span><span class="sxs-lookup"><span data-stu-id="393f5-172">Replace the contents of *Views/HelloWorld/Welcome.cshtml* with the following:</span></span>

[!code-html[Main](../../tutorials/first-mvc-app/start-mvc/sample/MvcMovie/Views/HelloWorld/Welcome.cshtml)]

<span data-ttu-id="393f5-173">Salvare le modifiche e passare all'URL seguente:</span><span class="sxs-lookup"><span data-stu-id="393f5-173">Save your changes and browse to the following URL:</span></span>

`http://localhost:xxxx/HelloWorld/Welcome?name=Rick&numtimes=4`

<span data-ttu-id="393f5-174">I dati vengono prelevati dall'URL e passati al controller usando lo [strumento di associazione di modelli MVC](xref:mvc/models/model-binding).</span><span class="sxs-lookup"><span data-stu-id="393f5-174">Data is taken from the URL and passed to the controller using the [MVC model binder](xref:mvc/models/model-binding) .</span></span> <span data-ttu-id="393f5-175">Il controller crea un pacchetto di dati in un dizionario `ViewData` e passa tale oggetto alla vista.</span><span class="sxs-lookup"><span data-stu-id="393f5-175">The controller packages the data into a `ViewData` dictionary and passes that object to the view.</span></span> <span data-ttu-id="393f5-176">La vista esegue quindi il rendering dei dati in formato HTML al browser.</span><span class="sxs-lookup"><span data-stu-id="393f5-176">The view then renders the data as HTML to the browser.</span></span>

![Vista About (Informazioni su) con un'etichetta di benvenuto e la frase Hello Rick riportata quattro volte](../../tutorials/first-mvc-app/adding-view/_static/rick2.png)

<span data-ttu-id="393f5-178">Nell'esempio precedente è stato usato il dizionario `ViewData` per passare i dati dal controller a una vista.</span><span class="sxs-lookup"><span data-stu-id="393f5-178">In the sample above, we used the `ViewData` dictionary to pass data from the controller to a view.</span></span> <span data-ttu-id="393f5-179">Più avanti nell'esercitazione si userà un modello di vista per passare i dati da un controller a una vista.</span><span class="sxs-lookup"><span data-stu-id="393f5-179">Later in the tutorial, we will use a view model to pass data from a controller to a view.</span></span> <span data-ttu-id="393f5-180">In genere l'approccio basato sul modello di vista per passare i dati è preferito rispetto all'approccio basato sul dizionario `ViewData`.</span><span class="sxs-lookup"><span data-stu-id="393f5-180">The view model approach to passing data is generally much preferred over the `ViewData` dictionary approach.</span></span> <span data-ttu-id="393f5-181">Per altre informazioni, vedere [ViewModel vs ViewData vs ViewBag vs TempData vs Session in MVC](http://www.mytecbits.com/microsoft/dot-net/viewmodel-viewdata-viewbag-tempdata-mvc) (Confronto tra ViewModel, ViewData, ViewBag, TempData e Session in MVC).</span><span class="sxs-lookup"><span data-stu-id="393f5-181">See [ViewModel vs ViewData vs ViewBag vs TempData vs Session in MVC](http://www.mytecbits.com/microsoft/dot-net/viewmodel-viewdata-viewbag-tempdata-mvc) for more information.</span></span>

<span data-ttu-id="393f5-182">Queste operazioni hanno riguardato un tipo di "M" per modello, ma non il tipo di database.</span><span class="sxs-lookup"><span data-stu-id="393f5-182">Well, that was a kind of an "M" for model, but not the database kind.</span></span> <span data-ttu-id="393f5-183">Creare un database di film con i concetti appresi.</span><span class="sxs-lookup"><span data-stu-id="393f5-183">Let's take what we've learned and create a database of movies.</span></span>