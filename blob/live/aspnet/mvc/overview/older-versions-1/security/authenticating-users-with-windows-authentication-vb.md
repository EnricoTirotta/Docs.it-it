---
uid: mvc/overview/older-versions-1/security/authenticating-users-with-windows-authentication-vb
title: L'autenticazione degli utenti con l'autenticazione di Windows (VB) | Documenti Microsoft
author: microsoft
description: Informazioni su come utilizzare l'autenticazione di Windows nel contesto di un'applicazione MVC. Viene descritto come abilitare l'autenticazione di Windows all'interno di co web dell'applicazione...
ms.author: aspnetcontent
manager: wpickett
ms.date: 01/27/2009
ms.topic: article
ms.assetid: 532fa051-7d5c-4d6d-87f6-339ce4b84c44
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions-1/security/authenticating-users-with-windows-authentication-vb
msc.type: authoredcontent
ms.openlocfilehash: d4b83d99fcf1247d08ce83364cc00e738b6a16c8
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2017
---
<a name="authenticating-users-with-windows-authentication-vb"></a><span data-ttu-id="a7f30-104">L'autenticazione degli utenti con l'autenticazione di Windows (VB)</span><span class="sxs-lookup"><span data-stu-id="a7f30-104">Authenticating Users with Windows Authentication (VB)</span></span>
====================
<span data-ttu-id="a7f30-105">da [Microsoft](https://github.com/microsoft)</span><span class="sxs-lookup"><span data-stu-id="a7f30-105">by [Microsoft](https://github.com/microsoft)</span></span>

> <span data-ttu-id="a7f30-106">Informazioni su come utilizzare l'autenticazione di Windows nel contesto di un'applicazione MVC.</span><span class="sxs-lookup"><span data-stu-id="a7f30-106">Learn how to use Windows authentication in the context of an MVC application.</span></span> <span data-ttu-id="a7f30-107">Informazioni su come abilitare l'autenticazione di Windows all'interno di file di configurazione dell'applicazione web e come configurare l'autenticazione con IIS.</span><span class="sxs-lookup"><span data-stu-id="a7f30-107">You learn how to enable Windows authentication within your application's web configuration file and how to configure authentication with IIS.</span></span> <span data-ttu-id="a7f30-108">Infine, è illustrato come utilizzare l'attributo [Authorize] per limitare l'accesso alle azioni del controller a gruppi o utenti specifici di Windows.</span><span class="sxs-lookup"><span data-stu-id="a7f30-108">Finally, you learn how to use the [Authorize] attribute to restrict access to controller actions to particular Windows users or groups.</span></span>


<span data-ttu-id="a7f30-109">L'obiettivo di questa esercitazione viene illustrato come è possibile usufruire di sicurezza funzionalità incorporate in Internet Information Services password proteggere le viste nelle applicazioni MVC.</span><span class="sxs-lookup"><span data-stu-id="a7f30-109">The goal of this tutorial is to explain how you can take advantage of the security features built into Internet Information Services to password protect the views in your MVC applications.</span></span> <span data-ttu-id="a7f30-110">Informazioni su come consentire azioni del controller da richiamare solo da utenti specifici di Windows o gli utenti che sono membri di determinati gruppi di Windows.</span><span class="sxs-lookup"><span data-stu-id="a7f30-110">You learn how to allow controller actions to be invoked only by particular Windows users or users who are members of particular Windows groups.</span></span>

<span data-ttu-id="a7f30-111">Utilizzando l'autenticazione di Windows ha senso quando si compila un sito Web interno aziendale (un sito intranet) e si desidera che gli utenti siano in grado di utilizzare i relativi nomi utente di Windows standard e una password per l'accesso del sito Web.</span><span class="sxs-lookup"><span data-stu-id="a7f30-111">Using Windows authentication makes sense when you are building an internal company website (an intranet site) and you want your users to be able to use their standard Windows user names and passwords when accessing the website.</span></span> <span data-ttu-id="a7f30-112">Se si sta compilando un verso l'esterno affiancate sito Web (un sito Web Internet) provare a utilizzare autenticazione basata su form.</span><span class="sxs-lookup"><span data-stu-id="a7f30-112">If you are building an outwards facing website (an Internet website) consider using Forms authentication instead.</span></span>

#### <a name="enabling-windows-authentication"></a><span data-ttu-id="a7f30-113">Abilitazione dell'autenticazione di Windows</span><span class="sxs-lookup"><span data-stu-id="a7f30-113">Enabling Windows Authentication</span></span>

<span data-ttu-id="a7f30-114">Quando si crea una nuova applicazione MVC ASP.NET, l'autenticazione di Windows non è abilitata per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="a7f30-114">When you create a new ASP.NET MVC application, Windows authentication is not enabled by default.</span></span> <span data-ttu-id="a7f30-115">Autenticazione basata su form è il tipo di autenticazione predefinito è abilitato per applicazioni MVC.</span><span class="sxs-lookup"><span data-stu-id="a7f30-115">Forms authentication is the default authentication type enabled for MVC applications.</span></span> <span data-ttu-id="a7f30-116">Modificando i file di configurazione (Web. config) web dell'applicazione MVC, è necessario abilitare l'autenticazione di Windows.</span><span class="sxs-lookup"><span data-stu-id="a7f30-116">You must enable Windows authentication by modifying your MVC application's web configuration (web.config) file.</span></span> <span data-ttu-id="a7f30-117">Trovare il &lt;autenticazione&gt; sezione e modificarlo per utilizzare Windows anziché l'autenticazione basata su form simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="a7f30-117">Find the &lt;authentication&gt; section and modify it to use Windows instead of Forms authentication like this:</span></span>

[!code-xml[Main](authenticating-users-with-windows-authentication-vb/samples/sample1.xml)]

<span data-ttu-id="a7f30-118">Quando si abilita l'autenticazione di Windows, server web diventa responsabile per l'autenticazione degli utenti.</span><span class="sxs-lookup"><span data-stu-id="a7f30-118">When you enable Windows authentication, your web server becomes responsible for authenticating users.</span></span> <span data-ttu-id="a7f30-119">In genere, esistono due tipi diversi di server web che utilizzano durante la creazione e distribuzione di un'applicazione ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="a7f30-119">Typically, there are two different types of web servers that you use when creating and deploying an ASP.NET MVC application.</span></span>

<span data-ttu-id="a7f30-120">In primo luogo, durante lo sviluppo di un'applicazione MVC, utilizzare il Server Web di sviluppo ASP.NET incluso in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a7f30-120">First, while developing an MVC application, you use the ASP.NET Development Web Server included with Visual Studio.</span></span> <span data-ttu-id="a7f30-121">Per impostazione predefinita, il Server Web di sviluppo ASP.NET esegue tutte le pagine nel contesto dell'account di Windows corrente (qualsiasi altro account utilizzato per l'accesso in Windows).</span><span class="sxs-lookup"><span data-stu-id="a7f30-121">By default, the ASP.NET Development Web Server executes all pages in the context of the current Windows account (whatever account you used to log into Windows).</span></span>

<span data-ttu-id="a7f30-122">Il Server Web di sviluppo ASP.NET supporta anche l'autenticazione NTLM.</span><span class="sxs-lookup"><span data-stu-id="a7f30-122">The ASP.NET Development Web Server also supports NTLM authentication.</span></span> <span data-ttu-id="a7f30-123">È possibile abilitare l'autenticazione NTLM facendo clic il nome del progetto nella finestra Esplora soluzioni e scegliendo proprietà.</span><span class="sxs-lookup"><span data-stu-id="a7f30-123">You can enable NTLM authentication by right-clicking the name of your project in the Solution Explorer window and selecting Properties.</span></span> <span data-ttu-id="a7f30-124">Successivamente, selezionare la scheda Web e selezionare la casella di controllo NTLM (vedere la figura 1).</span><span class="sxs-lookup"><span data-stu-id="a7f30-124">Next, select the Web tab and check the NTLM checkbox (see Figure 1).</span></span>

<span data-ttu-id="a7f30-125">**Figura 1: abilitare l'autenticazione NTLM per il Server Web di sviluppo ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="a7f30-125">**Figure 1 – Enabling NTLM authentication for the ASP.NET Development Web Server**</span></span>

![clip_image002](authenticating-users-with-windows-authentication-vb/_static/image1.jpg)

<span data-ttu-id="a7f30-127">Per un'applicazione web di produzione, l'icona della mano, si utilizza IIS come server web.</span><span class="sxs-lookup"><span data-stu-id="a7f30-127">For a production web application, on the hand, you use IIS as your web server.</span></span> <span data-ttu-id="a7f30-128">IIS supporta vari tipi di autenticazione tra cui:</span><span class="sxs-lookup"><span data-stu-id="a7f30-128">IIS supports several types of authentication including:</span></span>

- <span data-ttu-id="a7f30-129">L'autenticazione di base, definito come parte del protocollo HTTP 1.0.</span><span class="sxs-lookup"><span data-stu-id="a7f30-129">Basic Authentication – Defined as part of the HTTP 1.0 protocol.</span></span> <span data-ttu-id="a7f30-130">Invia i nomi utente e password in testo non crittografato (codificata Base64) tramite Internet.</span><span class="sxs-lookup"><span data-stu-id="a7f30-130">Sends user names and passwords in clear text (Base64 encoded) across the Internet.</span></span> <span data-ttu-id="a7f30-131">-L'autenticazione del Digest: invia un hash di una password, anziché la password, in internet.</span><span class="sxs-lookup"><span data-stu-id="a7f30-131">- Digest Authentication – Sends a hash of a password, instead of the password itself, across the internet.</span></span> <span data-ttu-id="a7f30-132">-Autenticazione integrata di Windows (NTLM) – il tipo di autenticazione da utilizzare in ambienti intranet mediante windows.</span><span class="sxs-lookup"><span data-stu-id="a7f30-132">- Integrated Windows (NTLM) Authentication – The best type of authentication to use in intranet environments using windows.</span></span> <span data-ttu-id="a7f30-133">-Certificati di autenticazione: abilita l'autenticazione utilizzando un certificato sul lato client.</span><span class="sxs-lookup"><span data-stu-id="a7f30-133">- Certificate Authentication – Enables authentication using a client-side certificate.</span></span> <span data-ttu-id="a7f30-134">Il certificato viene mappato a un account utente di Windows.</span><span class="sxs-lookup"><span data-stu-id="a7f30-134">The certificate maps to a Windows user account.</span></span>

> [!NOTE] 
> 
> <span data-ttu-id="a7f30-135">Per una panoramica più dettagliata di questi diversi tipi di autenticazione, vedere [https://msdn.microsoft.com/en-us/library/aa292114(VS.71).aspx](https://msdn.microsoft.com/en-us/library/aa292114(VS.71).aspx).</span><span class="sxs-lookup"><span data-stu-id="a7f30-135">For a more detailed overview of these different types of authentication, see [https://msdn.microsoft.com/en-us/library/aa292114(VS.71).aspx](https://msdn.microsoft.com/en-us/library/aa292114(VS.71).aspx).</span></span>


<span data-ttu-id="a7f30-136">Per abilitare un particolare tipo di autenticazione, è possibile utilizzare Gestione Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="a7f30-136">You can use Internet Information Services Manager to enable a particular type of authentication.</span></span> <span data-ttu-id="a7f30-137">Tenere presente che tutti i tipi di autenticazione non sono disponibili nel caso di ogni sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="a7f30-137">Be aware that all types of authentication are not available in the case of every operating system.</span></span> <span data-ttu-id="a7f30-138">Inoltre, se si utilizza IIS 7.0 con Windows Vista, è necessario abilitare i diversi tipi di autenticazione di Windows prima che vengano visualizzati in Gestione Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="a7f30-138">Furthermore, if you are using IIS 7.0 with Windows Vista, you will need to enable the different types of Windows authentication before they appear in the Internet Information Services Manager.</span></span> <span data-ttu-id="a7f30-139">Aprire **Pannello di controllo, programmi, programmi e funzionalità, delle funzionalità Windows attivare o disattivare**, espandere il nodo di Internet Information Services (vedere la figura 2).</span><span class="sxs-lookup"><span data-stu-id="a7f30-139">Open **Control Panel, Programs, Programs and Features, Turn Windows features on or off**, and expand the Internet Information Services node (see Figure 2).</span></span>

<span data-ttu-id="a7f30-140">**Figura 2: funzionalità di attivazione Windows IIS**</span><span class="sxs-lookup"><span data-stu-id="a7f30-140">**Figure 2 – Enabling Windows IIS features**</span></span>

![clip_image004](authenticating-users-with-windows-authentication-vb/_static/image2.jpg)

<span data-ttu-id="a7f30-142">Se si utilizza Internet Information Services, è possibile abilitare o disabilitare diversi tipi di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="a7f30-142">Using Internet Information Services, you can enable or disable different types of authentication.</span></span> <span data-ttu-id="a7f30-143">Ad esempio, la figura 3 illustra l'autenticazione anonima disabilitazione e abilitazione dell'autenticazione integrata di Windows (NTLM) quando si utilizza IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="a7f30-143">For example, Figure 3 illustrates disabling anonymous authentication and enabling Integrated Windows (NTLM) authentication when using IIS 7.0.</span></span>

<span data-ttu-id="a7f30-144">**Figura 3: abilitazione dell'autenticazione integrata di Windows**</span><span class="sxs-lookup"><span data-stu-id="a7f30-144">**Figure 3 – Enabling Integrated Windows Authentication**</span></span>

![clip_image006](authenticating-users-with-windows-authentication-vb/_static/image3.jpg)

#### <a name="authorizing-windows-users-and-groups"></a><span data-ttu-id="a7f30-146">Autorizzazione Windows utenti e gruppi</span><span class="sxs-lookup"><span data-stu-id="a7f30-146">Authorizing Windows Users and Groups</span></span>

<span data-ttu-id="a7f30-147">Dopo aver abilitato l'autenticazione di Windows, è possibile utilizzare il &lt;Authorize&gt; attributo per controllare l'accesso ai controller o le azioni del controller.</span><span class="sxs-lookup"><span data-stu-id="a7f30-147">After you enable Windows authentication, you can use the &lt;Authorize&gt; attribute to control access to controllers or controller actions.</span></span> <span data-ttu-id="a7f30-148">Questo attributo può essere applicato a un controller MVC intero o un'azione del controller specifico.</span><span class="sxs-lookup"><span data-stu-id="a7f30-148">This attribute can be applied to an entire MVC controller or a particular controller action.</span></span>

<span data-ttu-id="a7f30-149">Ad esempio, il controller Home nel listato 1 espone tre azioni denominate Index (), CompanySecrets() e StephenSecrets().</span><span class="sxs-lookup"><span data-stu-id="a7f30-149">For example, the Home controller in Listing 1 exposes three actions named Index(), CompanySecrets(), and StephenSecrets().</span></span> <span data-ttu-id="a7f30-150">Chiunque può richiamare l'azione Index ().</span><span class="sxs-lookup"><span data-stu-id="a7f30-150">Anyone can invoke the Index() action.</span></span> <span data-ttu-id="a7f30-151">Tuttavia, solo i membri del gruppo di responsabili locale di Windows possono richiamare l'azione di CompanySecrets().</span><span class="sxs-lookup"><span data-stu-id="a7f30-151">However, only members of the Windows local Managers group can invoke the CompanySecrets() action.</span></span> <span data-ttu-id="a7f30-152">Infine, solo l'utente di dominio Windows denominato Stephen (nel dominio Redmond) è possibile richiamare l'azione StephenSecrets().</span><span class="sxs-lookup"><span data-stu-id="a7f30-152">Finally, only the Windows domain user named Stephen (in the Redmond domain) can invoke the StephenSecrets() action.</span></span>

<span data-ttu-id="a7f30-153">**Elenco 1 – Controllers\HomeController.vb**</span><span class="sxs-lookup"><span data-stu-id="a7f30-153">**Listing 1 – Controllers\HomeController.vb**</span></span>

[!code-vb[Main](authenticating-users-with-windows-authentication-vb/samples/sample2.vb)]

> [!NOTE]
> <span data-ttu-id="a7f30-154">A causa di Windows controllo Account utente (UAC), quando si utilizza Windows Vista o Windows Server 2008, il gruppo Administrators locale si comporterà in modo diverso rispetto ad altri gruppi.</span><span class="sxs-lookup"><span data-stu-id="a7f30-154">Because of Windows User Account Control (UAC), when working with Windows Vista or Windows Server 2008, the local Administrators group will behave differently than other groups.</span></span> <span data-ttu-id="a7f30-155">Il &lt;Authorize&gt; attributo non riconosce un membro del gruppo Administrators locale a meno che non è modificare le impostazioni di controllo dell'account utente del computer.</span><span class="sxs-lookup"><span data-stu-id="a7f30-155">The &lt;Authorize&gt; attribute won't correctly recognize a member of the local Administrators group unless you modify your computer's UAC settings.</span></span>


<span data-ttu-id="a7f30-156">Esattamente cosa accade quando si tenta di richiamare un'azione del controller senza le autorizzazioni appropriate dipende dal tipo di autenticazione abilitato.</span><span class="sxs-lookup"><span data-stu-id="a7f30-156">Exactly what happens when you attempt to invoke a controller action without being the right permissions depends on the type of authentication enabled.</span></span> <span data-ttu-id="a7f30-157">Per impostazione predefinita, quando si utilizza il Server di sviluppo ASP.NET, è sufficiente ottenere una pagina vuota.</span><span class="sxs-lookup"><span data-stu-id="a7f30-157">By default, when using the ASP.NET Development Server, you simply get a blank page.</span></span> <span data-ttu-id="a7f30-158">Viene visualizzata la pagina con un **401 non autorizzato** stato della risposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7f30-158">The page is served with a **401 Not Authorized** HTTP Response Status.</span></span>

<span data-ttu-id="a7f30-159">Se, invece, si utilizza IIS con l'autenticazione anonima sia disabilitata e abilitata l'autenticazione di base, quindi consente di accedere a un prompt della finestra di dialogo account di accesso ogni volta che si richiede la pagina protetta (vedere la figura 4).</span><span class="sxs-lookup"><span data-stu-id="a7f30-159">If, on the other hand, you are using IIS with Anonymous authentication disabled and Basic authentication enabled, then you keep getting a login dialog prompt each time you request the protected page (see Figure 4).</span></span>

<span data-ttu-id="a7f30-160">**Figura 4-finestra di dialogo account di accesso autenticazione di base**</span><span class="sxs-lookup"><span data-stu-id="a7f30-160">**Figure 4 – Basic authentication login dialog**</span></span>

![clip_image008](authenticating-users-with-windows-authentication-vb/_static/image4.jpg)

#### <a name="summary"></a><span data-ttu-id="a7f30-162">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="a7f30-162">Summary</span></span>

<span data-ttu-id="a7f30-163">In questa esercitazione viene illustrato come è possibile utilizzare l'autenticazione di Windows nel contesto di un'applicazione MVC ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a7f30-163">This tutorial explained how you can use Windows authentication in the context of an ASP.NET MVC application.</span></span> <span data-ttu-id="a7f30-164">È stato descritto come abilitare l'autenticazione di Windows all'interno di file di configurazione dell'applicazione web e come configurare l'autenticazione con IIS.</span><span class="sxs-lookup"><span data-stu-id="a7f30-164">You learned how to enable Windows authentication within your application's web configuration file and how to configure authentication with IIS.</span></span> <span data-ttu-id="a7f30-165">Infine, si è appreso come utilizzare il &lt;Authorize&gt; attributo per limitare l'accesso alle azioni del controller a gruppi o utenti specifici di Windows.</span><span class="sxs-lookup"><span data-stu-id="a7f30-165">Finally, you learned how to use the &lt;Authorize&gt; attribute to restrict access to controller actions to particular Windows users or groups.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="a7f30-166">[Precedente](authenticating-users-with-forms-authentication-vb.md)
[Successivo](preventing-javascript-injection-attacks-vb.md)</span><span class="sxs-lookup"><span data-stu-id="a7f30-166">[Previous](authenticating-users-with-forms-authentication-vb.md)
[Next](preventing-javascript-injection-attacks-vb.md)</span></span>