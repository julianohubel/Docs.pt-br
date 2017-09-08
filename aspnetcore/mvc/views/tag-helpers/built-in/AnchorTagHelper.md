---
title: Auxiliar de marca de ancoragem | Microsoft Docs
author: pkellner
description: "Mostra como trabalhar com o auxiliar de marca de âncora"
keywords: ASP.NET Core, o auxiliar de marca
ms.author: riande
manager: wpickett
ms.date: 02/14/2017
ms.topic: article
ms.assetid: c045d485-d1dc-4cea-a675-46be83b7a011
ms.technology: aspnet
ms.prod: aspnet-core
uid: mvc/views/tag-helpers/builtin-th/AnchorTagHelper
ms.openlocfilehash: f08e6a5288076d56b55843f1872bcfa8104f3923
ms.sourcegitcommit: 0b6c8e6d81d2b3c161cd375036eecbace46a9707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2017
---
# <a name="anchor-tag-helper"></a><span data-ttu-id="b2b31-104">Auxiliar de marca de âncora</span><span class="sxs-lookup"><span data-stu-id="b2b31-104">Anchor Tag Helper</span></span>

<span data-ttu-id="b2b31-105">Por [Peter Kellner](http://peterkellner.net)</span><span class="sxs-lookup"><span data-stu-id="b2b31-105">By [Peter Kellner](http://peterkellner.net)</span></span> 

<span data-ttu-id="b2b31-106">O auxiliar de marca de âncora aprimora a âncora HTML (`<a ... ></a>`) marca adicionando novos atributos.</span><span class="sxs-lookup"><span data-stu-id="b2b31-106">The Anchor Tag Helper enhances the HTML anchor (`<a ... ></a>`) tag by adding new attributes.</span></span> <span data-ttu-id="b2b31-107">O link gerado (no `href` marca) é criado usando os novos atributos.</span><span class="sxs-lookup"><span data-stu-id="b2b31-107">The link generated (on the `href` tag) is created using the new attributes.</span></span> <span data-ttu-id="b2b31-108">Essa URL pode incluir um protocolo opcional, como HTTP.</span><span class="sxs-lookup"><span data-stu-id="b2b31-108">That URL can include an optional protocol such as https.</span></span>

<span data-ttu-id="b2b31-109">O controlador do apresentador abaixo é usado nos exemplos neste documento.</span><span class="sxs-lookup"><span data-stu-id="b2b31-109">The speaker controller below is used in samples in this document.</span></span>

<br/><span data-ttu-id="b2b31-110">
**SpeakerController.cs**</span><span class="sxs-lookup"><span data-stu-id="b2b31-110">
**SpeakerController.cs**</span></span> 

<span data-ttu-id="b2b31-111">[!code-csharp[SpeakerController](sample/TagHelpersBuiltInAspNetCore/src/TagHelpersBuiltInAspNetCore/Controllers/SpeakerController.cs)]</span><span class="sxs-lookup"><span data-stu-id="b2b31-111">[!code-csharp[SpeakerController](sample/TagHelpersBuiltInAspNetCore/src/TagHelpersBuiltInAspNetCore/Controllers/SpeakerController.cs)]</span></span>


## <a name="anchor-tag-helper-attributes"></a><span data-ttu-id="b2b31-112">Atributos de auxiliar de marca de âncora</span><span class="sxs-lookup"><span data-stu-id="b2b31-112">Anchor Tag Helper Attributes</span></span>

- - -

### <a name="asp-controller"></a><span data-ttu-id="b2b31-113">controlador de ASP</span><span class="sxs-lookup"><span data-stu-id="b2b31-113">asp-controller</span></span>

<span data-ttu-id="b2b31-114">`asp-controller`é usado para associar o controlador será usado para gerar a URL.</span><span class="sxs-lookup"><span data-stu-id="b2b31-114">`asp-controller` is used to associate which controller will be used to generate the URL.</span></span> <span data-ttu-id="b2b31-115">Os controladores especificados devem existir no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="b2b31-115">The controllers specified must exist in the current project.</span></span> <span data-ttu-id="b2b31-116">O código a seguir lista todos os alto-falantes:</span><span class="sxs-lookup"><span data-stu-id="b2b31-116">The following code lists all speakers:</span></span> 

```cshtml
<a asp-controller="Speaker" asp-action="Index">All Speakers</a>
```

<span data-ttu-id="b2b31-117">A marcação gerada será:</span><span class="sxs-lookup"><span data-stu-id="b2b31-117">The generated markup will be:</span></span>

```html
<a href="/Speaker">All Speakers</a>
```

<span data-ttu-id="b2b31-118">Se o `asp-controller` for especificado e `asp-action` não, é o padrão `asp-action` será o método do controlador padrão do modo de exibição atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="b2b31-118">If the `asp-controller` is specified and `asp-action` is not, the default `asp-action` will be the default controller method of the currently executing view.</span></span> <span data-ttu-id="b2b31-119">Que é, no exemplo acima, se `asp-action` é à esquerda, e este auxiliar de marca de âncora é gerado a partir *HomeController*do `Index` exibição (**/home**), a marcação gerada será:</span><span class="sxs-lookup"><span data-stu-id="b2b31-119">That is, in the above example, if `asp-action` is left out, and this Anchor Tag Helper is generated from *HomeController*'s `Index` view (**/Home**), the generated markup will be:</span></span>


```html
<a href="/Home">All Speakers</a>
```

- - -
  
### <a name="asp-action"></a><span data-ttu-id="b2b31-120">ação de ASP</span><span class="sxs-lookup"><span data-stu-id="b2b31-120">asp-action</span></span>

<span data-ttu-id="b2b31-121">`asp-action`é o nome do método de ação no controlador que serão incluído no gerado `href`.</span><span class="sxs-lookup"><span data-stu-id="b2b31-121">`asp-action` is the name of the action method in the controller that will be included in the generated `href`.</span></span> <span data-ttu-id="b2b31-122">Por exemplo, o código a seguir defina gerado `href` para apontar para a página de detalhes do apresentador:</span><span class="sxs-lookup"><span data-stu-id="b2b31-122">For example, the following code set the generated `href` to point to the speaker detail page:</span></span>

```html
<a asp-controller="Speaker" asp-action="Detail">Speaker Detail</a>
```

<span data-ttu-id="b2b31-123">A marcação gerada será:</span><span class="sxs-lookup"><span data-stu-id="b2b31-123">The generated markup will be:</span></span>

```html
<a href="/Speaker/Detail">Speaker Detail</a>
```

<span data-ttu-id="b2b31-124">Se nenhum `asp-controller` atributo for especificado, o controlador padrão chamando o modo de exibição que executar a exibição atual será usado.</span><span class="sxs-lookup"><span data-stu-id="b2b31-124">If no `asp-controller` attribute is specified, the default controller calling the view executing the current view will be used.</span></span>  
 
<span data-ttu-id="b2b31-125">Se o atributo `asp-action` é `Index`, em seguida, nenhuma ação é anexada à URL, à esquerda para o padrão `Index` método ser chamado.</span><span class="sxs-lookup"><span data-stu-id="b2b31-125">If the attribute `asp-action` is `Index`, then no action is appended to the URL, leading to the default `Index` method being called.</span></span> <span data-ttu-id="b2b31-126">A ação especificada (ou padrão), deve existir no controlador referenciado em `asp-controller`.</span><span class="sxs-lookup"><span data-stu-id="b2b31-126">The action specified (or defaulted), must exist in the controller referenced in `asp-controller`.</span></span>

- - -
  
<a name="route"></a>
### <a name="asp-route-value"></a><span data-ttu-id="b2b31-127">ASP - rota-{value}</span><span class="sxs-lookup"><span data-stu-id="b2b31-127">asp-route-{value}</span></span>

<span data-ttu-id="b2b31-128">`asp-route-`é um prefixo de rota de curinga.</span><span class="sxs-lookup"><span data-stu-id="b2b31-128">`asp-route-` is a wild card route prefix.</span></span> <span data-ttu-id="b2b31-129">Qualquer valor colocado após o traço à direita será interpretado como um parâmetro de rota potencial.</span><span class="sxs-lookup"><span data-stu-id="b2b31-129">Any value you put after the trailing dash will be interpreted as a potential route parameter.</span></span> <span data-ttu-id="b2b31-130">Se uma rota padrão não for encontrada, esse prefixo de rota será anexado para o href gerado como um parâmetro de solicitação e um valor.</span><span class="sxs-lookup"><span data-stu-id="b2b31-130">If a default route is not found, this route prefix will be appended to the generated href as a request parameter and value.</span></span> <span data-ttu-id="b2b31-131">Caso contrário, ele será substituído no modelo de rota.</span><span class="sxs-lookup"><span data-stu-id="b2b31-131">Otherwise it will be substituted in the route template.</span></span>

<span data-ttu-id="b2b31-132">Supondo que você tenha um método de controlador definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b2b31-132">Assuming you have a controller method defined as follows:</span></span>

```csharp
public IActionResult AnchorTagHelper(string id)
{
    var speaker = new SpeakerData()
    {
        SpeakerId = 12
    };      
    return View(viewName, speaker);
}
```

<span data-ttu-id="b2b31-133">E que o modelo de rota padrão definido no seu *Startup.cs* da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b2b31-133">And have the default route template defined in your *Startup.cs* as follows:</span></span>

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});

```

<span data-ttu-id="b2b31-134">O **cshtml** arquivo que contém o auxiliar de marca de âncora necessário usar o **locutor** parâmetro de modelo passado do controlador para o modo de exibição é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b2b31-134">The **cshtml** file that contains the Anchor Tag Helper necessary to use the **speaker** model parameter passed in from the controller to the view is as follows:</span></span>

```cshtml
@model SpeakerData
<!DOCTYPE html>
<html><body>
<a asp-controller='Speaker' asp-action='Detail' asp-route-id=@Model.SpeakerId>SpeakerId: @Model.SpeakerId</a>
<body></html>
```

<span data-ttu-id="b2b31-135">O código HTML gerado será da seguinte maneira porque **id** foi encontrado na rota padrão.</span><span class="sxs-lookup"><span data-stu-id="b2b31-135">The generated HTML will then be as follows because **id** was found in the default route.</span></span>

```html
<a href='/Speaker/Detail/12'>SpeakerId: 12</a>
```

<span data-ttu-id="b2b31-136">Se o prefixo da rota não é parte do modelo de roteamento encontrado, que é o caso com o seguinte **cshtml** arquivo:</span><span class="sxs-lookup"><span data-stu-id="b2b31-136">If the route prefix is not part of the routing template found, which is the case with the following **cshtml** file:</span></span>

```cshtml
@model SpeakerData
<!DOCTYPE html>
<html><body>
<a asp-controller='Speaker' asp-action='Detail' asp-route-speakerid=@Model.SpeakerId>SpeakerId: @Model.SpeakerId</a>
<body></html>
```

<span data-ttu-id="b2b31-137">O código HTML gerado será da seguinte maneira porque **speakerid** não foi encontrado na rota correspondida:</span><span class="sxs-lookup"><span data-stu-id="b2b31-137">The generated HTML will then be as follows because **speakerid** was not found in the route matched:</span></span>


```html
<a href='/Speaker/Detail?speakerid=12'>SpeakerId: 12</a>
```

<span data-ttu-id="b2b31-138">Se qualquer um dos `asp-controller` ou `asp-action` não forem especificados, e o processamento padrão mesmo é seguido porque está sendo o `asp-route` atributo.</span><span class="sxs-lookup"><span data-stu-id="b2b31-138">If either `asp-controller` or `asp-action` are not specified, then the same default processing is followed as is in the `asp-route` attribute.</span></span>

- - -

### <a name="asp-route"></a><span data-ttu-id="b2b31-139">rota de ASP</span><span class="sxs-lookup"><span data-stu-id="b2b31-139">asp-route</span></span>

<span data-ttu-id="b2b31-140">`asp-route`Fornece uma maneira de criar uma URL que vincula-se diretamente a uma rota nomeada.</span><span class="sxs-lookup"><span data-stu-id="b2b31-140">`asp-route` provides a way to create a URL that links directly to a named route.</span></span> <span data-ttu-id="b2b31-141">Usando atributos de roteamento, uma rota pode ser nomeada como mostra o `SpeakerController` e usado em seu `Evaluations` método.</span><span class="sxs-lookup"><span data-stu-id="b2b31-141">Using routing attributes, a route can be named as shown in the `SpeakerController` and used in its `Evaluations` method.</span></span>

<span data-ttu-id="b2b31-142">`Name = "speakerevals"`informa o auxiliar de marca de âncora para gerar uma rota diretamente para esse método de controlador usando a URL `/Speaker/Evaluations`.</span><span class="sxs-lookup"><span data-stu-id="b2b31-142">`Name = "speakerevals"` tells the Anchor Tag Helper to generate a route directly to that controller method using the URL `/Speaker/Evaluations`.</span></span> <span data-ttu-id="b2b31-143">Se `asp-controller` ou `asp-action` é especificado além `asp-route`, a rota gerada não pode ser o esperado.</span><span class="sxs-lookup"><span data-stu-id="b2b31-143">If `asp-controller` or `asp-action` is specified in addition to `asp-route`, the route generated may not be what you expect.</span></span> <span data-ttu-id="b2b31-144">`asp-route`não deve ser usada com qualquer um dos atributos `asp-controller` ou `asp-action` para evitar um conflito de rota.</span><span class="sxs-lookup"><span data-stu-id="b2b31-144">`asp-route` should not be used with either of the attributes `asp-controller` or `asp-action` to avoid a route conflict.</span></span>

- - -

### <a name="asp-all-route-data"></a><span data-ttu-id="b2b31-145">ASP-all-dados de rota</span><span class="sxs-lookup"><span data-stu-id="b2b31-145">asp-all-route-data</span></span>

<span data-ttu-id="b2b31-146">`asp-all-route-data`permite a criação de um dicionário de pares chave-valor em que a chave é o nome do parâmetro e o valor é o valor associado a essa chave.</span><span class="sxs-lookup"><span data-stu-id="b2b31-146">`asp-all-route-data` allows creating a dictionary of key value pairs where the key is the parameter name and the value is the value associated with that key.</span></span>

<span data-ttu-id="b2b31-147">Como o exemplo a seguir mostra, um dicionário embutido é criado e os dados são passados para o modo de exibição do razor.</span><span class="sxs-lookup"><span data-stu-id="b2b31-147">As the example below shows, an inline dictionary is created and the data is passed to the razor view.</span></span> <span data-ttu-id="b2b31-148">Como alternativa, os dados podem ser passados com seu modelo.</span><span class="sxs-lookup"><span data-stu-id="b2b31-148">As an alternative, the data could also be passed in with your model.</span></span>

```cshtml
@{
    var dict =
        new Dictionary<string, string>
        {
            {"speakerId", "11"},
            {"currentYear", "true"}
        };
}
<a asp-route="speakerevalscurrent" 
   asp-all-route-data="dict">SpeakerEvals</a>
```

<span data-ttu-id="b2b31-149">O código anterior gera a seguinte URL: http://localhost/Speaker/EvaluationsCurrent?speakerId=11&currentYear=true</span><span class="sxs-lookup"><span data-stu-id="b2b31-149">The code above generates the following URL: http://localhost/Speaker/EvaluationsCurrent?speakerId=11&currentYear=true</span></span>

<span data-ttu-id="b2b31-150">Quando o link é clicado, o método do controlador `EvaluationsCurrent` é chamado.</span><span class="sxs-lookup"><span data-stu-id="b2b31-150">When the link is clicked, the controller method `EvaluationsCurrent` is called.</span></span> <span data-ttu-id="b2b31-151">Ele é chamado porque esse controlador tem dois parâmetros de cadeia de caracteres que correspondem o que foi criado a partir de `asp-all-route-data` dicionário.</span><span class="sxs-lookup"><span data-stu-id="b2b31-151">It is called because that controller has two string parameters that match what has been created from the `asp-all-route-data` dictionary.</span></span>

<span data-ttu-id="b2b31-152">Se todas as chaves na correspondência de dicionário de parâmetros de rota, esses valores são substituídos na rota conforme apropriado e os outros valores não correspondentes serão gerados como parâmetros de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b2b31-152">If any keys in the dictionary match route parameters, those values will be substituted in the route as appropriate and the other non-matching values will be generated as request parameters.</span></span>

- - -

### <a name="asp-fragment"></a><span data-ttu-id="b2b31-153">fragmento de ASP</span><span class="sxs-lookup"><span data-stu-id="b2b31-153">asp-fragment</span></span>

<span data-ttu-id="b2b31-154">`asp-fragment`define um fragmento de URL para acrescentar à URL.</span><span class="sxs-lookup"><span data-stu-id="b2b31-154">`asp-fragment` defines a URL fragment to append to the URL.</span></span> <span data-ttu-id="b2b31-155">O auxiliar de marca de âncora adicionará o caractere de hash (#).</span><span class="sxs-lookup"><span data-stu-id="b2b31-155">The Anchor Tag Helper will add the hash character (#).</span></span> <span data-ttu-id="b2b31-156">Se você criar uma marca:</span><span class="sxs-lookup"><span data-stu-id="b2b31-156">If you create a tag:</span></span>

```cshtml
<a asp-action="Evaluations" asp-controller="Speaker"  
   asp-fragment="SpeakerEvaluations">About Speaker Evals</a>
```

<span data-ttu-id="b2b31-157">A URL gerada será: http://localhost/Speaker/Evaluations#SpeakerEvaluations</span><span class="sxs-lookup"><span data-stu-id="b2b31-157">The generated URL will be: http://localhost/Speaker/Evaluations#SpeakerEvaluations</span></span>

<span data-ttu-id="b2b31-158">Marcas de hash são úteis ao criar aplicativos do lado do cliente.</span><span class="sxs-lookup"><span data-stu-id="b2b31-158">Hash tags are useful when building client-side applications.</span></span> <span data-ttu-id="b2b31-159">Eles podem ser usados para marcar fácil e pesquisa em JavaScript, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="b2b31-159">They can be used for easy marking and searching in JavaScript, for example.</span></span>

- - -

### <a name="asp-area"></a><span data-ttu-id="b2b31-160">área de ASP</span><span class="sxs-lookup"><span data-stu-id="b2b31-160">asp-area</span></span>

<span data-ttu-id="b2b31-161">`asp-area`Define o nome da área que usa o ASP.NET Core para definir a rota apropriada.</span><span class="sxs-lookup"><span data-stu-id="b2b31-161">`asp-area` sets the area name that ASP.NET Core uses to set the appropriate route.</span></span> <span data-ttu-id="b2b31-162">A seguir estão exemplos de como o atributo área faz com que um remapeamento de rotas.</span><span class="sxs-lookup"><span data-stu-id="b2b31-162">Below are examples of how the area attribute causes a remapping of routes.</span></span> <span data-ttu-id="b2b31-163">Configuração `asp-area` blogs prefixos de diretório `Areas/Blogs` para as rotas do associado controladores e exibições para a marca de âncora.</span><span class="sxs-lookup"><span data-stu-id="b2b31-163">Setting `asp-area` to Blogs prefixes the directory `Areas/Blogs` to the routes of the associated controllers and views for this anchor tag.</span></span>

* <span data-ttu-id="b2b31-164">Nome do projeto</span><span class="sxs-lookup"><span data-stu-id="b2b31-164">Project name</span></span>

  * <span data-ttu-id="b2b31-165">*wwwroot*</span><span class="sxs-lookup"><span data-stu-id="b2b31-165">*wwwroot*</span></span>

  * <span data-ttu-id="b2b31-166">*Áreas*</span><span class="sxs-lookup"><span data-stu-id="b2b31-166">*Areas*</span></span>

    * <span data-ttu-id="b2b31-167">*Blogs*</span><span class="sxs-lookup"><span data-stu-id="b2b31-167">*Blogs*</span></span>

      * <span data-ttu-id="b2b31-168">*Controladores*</span><span class="sxs-lookup"><span data-stu-id="b2b31-168">*Controllers*</span></span>

        * <span data-ttu-id="b2b31-169">*HomeController*</span><span class="sxs-lookup"><span data-stu-id="b2b31-169">*HomeController.cs*</span></span>

      * <span data-ttu-id="b2b31-170">*Modos de exibição*</span><span class="sxs-lookup"><span data-stu-id="b2b31-170">*Views*</span></span>

        * <span data-ttu-id="b2b31-171">*Casa*</span><span class="sxs-lookup"><span data-stu-id="b2b31-171">*Home*</span></span>

          * <span data-ttu-id="b2b31-172">*Cshtml*</span><span class="sxs-lookup"><span data-stu-id="b2b31-172">*Index.cshtml*</span></span>
          
          * <span data-ttu-id="b2b31-173">*AboutBlog.cshtml*</span><span class="sxs-lookup"><span data-stu-id="b2b31-173">*AboutBlog.cshtml*</span></span>
          
  * <span data-ttu-id="b2b31-174">*Controladores*</span><span class="sxs-lookup"><span data-stu-id="b2b31-174">*Controllers*</span></span>
  

        
<span data-ttu-id="b2b31-175">Especificando uma marca de área é válida, como ```area="Blogs"``` ao referenciar o ```AboutBlog.cshtml``` arquivo será semelhante a seguir usando o auxiliar de marca de âncora.</span><span class="sxs-lookup"><span data-stu-id="b2b31-175">Specifying an area tag that is valid, such as ```area="Blogs"``` when referencing the ```AboutBlog.cshtml``` file will look like the following using the Anchor Tag Helper.</span></span>

```cshtml
<a asp-action="AboutBlog" asp-controller="Home" asp-area="Blogs">Blogs About</a>
```

<span data-ttu-id="b2b31-176">O código HTML gerado incluirá o segmento de áreas e será da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b2b31-176">The generated HTML will include the areas segment and will be as follows:</span></span>

```html
<a href="/Blogs/Home/AboutBlog">Blogs About</a>
```

> [!TIP]
> <span data-ttu-id="b2b31-177">Para as áreas do MVC trabalhar em um aplicativo web, o modelo de rota deve incluir uma referência para a área se ele existir.</span><span class="sxs-lookup"><span data-stu-id="b2b31-177">For MVC areas to work in a web application, the route template must include a reference to the area if it exists.</span></span> <span data-ttu-id="b2b31-178">Esse modelo, que é o segundo parâmetro do `routes.MapRoute` chamada de método, será exibida como:`template: '"{area:exists}/{controller=Home}/{action=Index}"'`</span><span class="sxs-lookup"><span data-stu-id="b2b31-178">That template, which is the second parameter of the `routes.MapRoute` method call, will appear as: `template: '"{area:exists}/{controller=Home}/{action=Index}"'`</span></span>

- - -

### <a name="asp-protocol"></a><span data-ttu-id="b2b31-179">protocolo de ASP</span><span class="sxs-lookup"><span data-stu-id="b2b31-179">asp-protocol</span></span>

<span data-ttu-id="b2b31-180">O `asp-protocol` é para especificar um protocolo (como `https`) em sua URL.</span><span class="sxs-lookup"><span data-stu-id="b2b31-180">The `asp-protocol` is for specifying a protocol (such as `https`) in your URL.</span></span> <span data-ttu-id="b2b31-181">Um auxiliar de marca de âncora que contenha o protocolo de exemplo será semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="b2b31-181">An example Anchor Tag Helper that includes the protocol will look as follows:</span></span>

```<a asp-protocol="https" asp-action="About" asp-controller="Home">About</a>```

<span data-ttu-id="b2b31-182">e irá gerar o HTML da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b2b31-182">and will generate HTML as follows:</span></span>

```<a href="https://localhost/Home/About">About</a>```

<span data-ttu-id="b2b31-183">O domínio no exemplo é localhost, mas o auxiliar de marca de âncora usará o domínio do site público ao gerar a URL.</span><span class="sxs-lookup"><span data-stu-id="b2b31-183">The domain in the example is localhost, but the Anchor Tag Helper uses the website's public domain when generating the URL.</span></span>

- - -

## <a name="additional-resources"></a><span data-ttu-id="b2b31-184">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b2b31-184">Additional resources</span></span>

* [<span data-ttu-id="b2b31-185">Áreas</span><span class="sxs-lookup"><span data-stu-id="b2b31-185">Areas</span></span>](xref:mvc/controllers/areas)