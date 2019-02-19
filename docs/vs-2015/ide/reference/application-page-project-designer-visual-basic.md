---
title: 專案設計工具、應用程式頁面 (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 21f94323fbfa7369e3fef93b0f95a8db2ea46ce2
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774856"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
使用 [專案設計工具] 的 [應用程式] 頁面來指定專案的應用程式設定和屬性。  
  
 若要存取 [應用程式] 頁面，請在方案總管中選擇專案節點 (而不是 [方案] 節點)。 然後選擇功能表列上的 [專案]、[屬性]。 [專案設計工具] 出現時，請按一下 [應用程式] 索引標籤。  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>一般應用程式設定  
 下列選項可讓您設定應用程式的一般設定。  
  
 **組件名稱**  
 指定將包含組件資訊清單之輸出檔的名稱。 如果您變更此屬性，也會變更 [輸出名稱] 屬性。 您也可以在命令提示字元使用 [/out (Visual Basic)](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) 進行這項變更。 如需如何以程式設計方式存取此屬性的資訊，請參閱 <xref:VSLangProj.ProjectProperties.AssemblyName%2A>。  
  
 **根命名空間**  
 指定專案中所有檔案的基底命名空間。 例如，如果您將 [根命名空間] 設為 `Project1`，而且您程式碼的任何命名空間外部有 `Class1`，則其命名空間為 `Project1.Class1`。 如果程式碼的命名空間 `Order` 中有 `Class2`，則其命名空間為 `Project1.Order.Class2`。  
  
 如果您清除 [根命名空間]，則可以在程式碼中指定專案的命名空間結構。  
  
> [!NOTE]
>  如果您在 [Namespace 陳述式](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2)中使用 Global 關鍵字，則可以從專案的根命名空間定義一個命名空間。 如果您清除 [根命名空間]，`Global` 會成為最上層命名空間，因此 `Namespace` 陳述式中不需要 `Global` 關鍵字。 如需詳細資訊，請參閱 [Visual Basic 中的命名空間](http://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88)中的＜Namespace 陳述式中的 Global 關鍵字＞。  
  
 如需如何在程式碼中建立命名空間的資訊，請參閱 [Namespace 陳述式](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2)。  
  
 如需根命名空間屬性的詳細資訊，請參閱 [/rootnamespace](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783)。  
  
 如需如何以程式設計方式存取此屬性的資訊，請參閱 <xref:VSLangProj.ProjectProperties.RootNamespace%2A>。  
  
 **目標架構 (所有組態)**  
 指定應用程式作為目標的 .NET Framework 版本。 此選項可能會有不同的值，而這些值取決於電腦上安裝的 .NET Framework 版本。  
  
 預設值會符合您在 [新增專案] 對話方塊中指定的目標架構。  
  
> [!NOTE]
>  第一次開啟該對話方塊時，會自動設定[必要條件對話方塊](../../ide/reference/prerequisites-dialog-box.md)中所列的必要條件套件。 如果您接著變更專案的目標架構，就必須手動指定必要條件以符合新的目標架構。  
  
 如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../../ide/how-to-target-a-version-of-the-dotnet-framework.md)和 [Visual Studio 多目標概觀](../../ide/visual-studio-multi-targeting-overview.md)。  
  
 **應用程式類型**  
 指定要建置的應用程式類型。 針對 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] 應用程式，您可以指定 [Windows 市集應用程式]、[類別庫] 或 [WinMD 檔案]。 針對大多數其他應用程式類型，您可以指定 [Windows 應用程式]、[主控台應用程式]、[類別庫]、[Windows 服務] 或 [Web 控制項程式庫]。  
  
 針對 Web 應用程式專案，您必須指定 [類別庫]。  
  
 如果您指定 [WinMD 檔案] 選項，則類型可以投影至任何 Windows 執行階段程式設計語言。 將專案的輸出封裝為 WinMD 檔案，即可使用多種語言來撰寫應用程式，並讓程式碼交互操作，如同您使用相同的語言來撰寫程式碼一樣。 您可以針對以 Windows 執行階段程式庫為目標的方案使用 [WinMD 檔案]選項，包括 [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] 應用程式。 如需詳細資訊，請參閱[在 C++ 和 Visual Basic 中建立 Windows 執行階段元件](http://go.microsoft.com/fwlink/?LinkId=231895)。  
  
> [!NOTE]
>  Windows 執行階段可以投影類型，以使用它們的語言顯示為原生物件。 例如，與 Windows 執行階段互動的 JavaScript 應用程式會使用它作為一組 JavaScript 物件，而且 C# 應用程式會使用該程式庫作為 .NET 物件集合。 將專案的輸出封裝為 WinMD 檔案，即可利用 Windows 執行階段所使用的相同技術。  
  
 如需 [應用程式類型] 屬性的詳細資訊，請參閱 [/target (Visual Basic)](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c)。 如需如何以程式設計方式存取該屬性的資訊，請參閱 <xref:VSLangProj.ProjectProperties.OutputType%2A>。  
  
 **圖示**  
 設定想要用來當作程式圖示的 .ico 檔案。 選取 [\<瀏覽...>]，以瀏覽現有圖形。 如需詳細資訊，請參閱 [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (或 [/win32icon (C# 編譯器選項)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138))。 若要以程式設計方式存取此屬性，請參閱 <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>。  
  
 **啟動表單/啟始物件/啟動 URI**  
 指定應用程式的啟動表單或進入點。  
  
 如果選取 [啟用應用程式架構]\(預設)，此清單的標題為 [啟動表單]，而且因為應用程式架構只支援啟動表單，而非物件，所以只會顯示表單。  
  
 如果專案是 WPF 瀏覽器應用程式，此清單的標題為 [啟動 URI]，而且預設值為 **Page1.xaml**。 [啟動 URI] 清單可讓您指定應用程式在啟動時顯示的使用者介面資源 (XAML 項目)。 如需詳細資訊，請參閱<xref:System.Windows.Application.StartupUri%2A>。  
  
 如果清除 [啟用應用程式架構]，此清單會成為 [啟始物件]，並顯示具有 `Sub Main` 的表單和類別或模組。  
  
 [啟始物件] 定義要在應用程式載入時呼叫的進入點。 通常，這會設定成您應用程式中的主要表單，或應該在應用程式啟動時執行的 `Sub Main` 處理序。 因為類別庫沒有進入點，所以這個屬性的唯一選項是 [(無)]。 如需詳細資訊，請參閱 [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0)。 若要以程式設計方式存取此屬性，請參閱 <xref:VSLangProj.ProjectProperties.StartupObject%2A>。  
  
 **組件資訊**  
 按一下此按鈕，以顯示[組件資訊對話方塊](../../ide/reference/assembly-information-dialog-box.md)。  
  
 **啟用應用程式架構**  
 指定專案是否使用應用程式架構。 此選項的設定會影響 [啟動表單]/[啟始物件] 中提供的選項。  
  
 如果選取此核取方塊，您的應用程式會使用標準 `Sub Main`。 選取此核取方塊可啟用 [Windows 應用程式架構屬性] 區段中的功能，也需要您選取啟動表單。  
  
 如果清除此核取方塊，則您的應用程式會使用 [啟動表單] 中所指定的自訂 `Sub Main`。 在此情況下，您可以指定啟始物件 (方法或類別中的自訂 `Sub Main`) 或表單。 此外，[Windows 應用程式架構屬性] 區段中的選項會變成無法使用。  
  
 **檢視 Windows 設定**  
 按一下此按鈕，以產生並開啟 app.manifest 檔案。 Visual Studio 會使用此檔案，來產生應用程式的資訊清單資料。 然後，修改 app.manifest 中的 `<requestedExecutionLevel>` 標記，來設定 UAC 要求執行層級，如下所示：  
  
 `<requestedExecutionLevel level="asInvoker" />`  
  
 ClickOnce 使用 `asInvoker` 層級或透過虛擬化模式 (無資訊清單產生)。 若要指定虛擬化模式，請從 app.manifest 中移除整個標記。  
  
 如需資訊清單產生的詳細資訊，請參閱 [Windows Vista 的 ClickOnce 部署](../../deployment/clickonce-deployment-on-windows-vista.md)。  
  
## <a name="windows-application-framework-properties"></a>Windows 應用程式架構屬性  
 [Windows 應用程式架構屬性] 區段中具有下列設定。 只有在選取 [啟用應用程式架構] 核取方塊時，才能使用這些選項。 後續區段描述 Windows Presentation Foundation (WPF) 應用程式的 [Windows 應用程式架構屬性] 設定。  
  
 **啟用 XP 視覺化樣式**  
 啟用或停用 Windows XP 視覺化樣式，也稱為 [Windows XP 佈景主題]。 例如，Windows XP 視覺化樣式會啟用具有圓角和動態色彩的控制項。 會啟用預設值。 如需 Windows XP 視覺化樣式的詳細資訊，請參閱 [Windows XP 功能和 Windows Form 控制項](http://msdn.microsoft.com/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0))。  
  
 **建立單一執行個體應用程式**  
 選取此核取方塊，來防止使用者執行應用程式的多個執行個體。 此核取方塊的預設設定會予以清除。 此設定允許執行應用程式的多個執行個體。  
  
 **程式關閉時儲存 My.Settings**  
 選取此核取方塊，來指定使用者關閉其電腦時儲存的應用程式 `My.Settings` 設定。 會啟用預設設定。 如果停用此選項，您可以呼叫 `My.Settings.Save`，來手動儲存應用程式設定。  
  
 **驗證模式**  
 選取 [Windows]\(預設)，來指定使用 Windows 驗證來識別目前登入的使用者。 您可以使用 `My.User` 物件，在執行階段擷取這項資訊。 如果您要提供自己的程式碼來驗證使用者，而不是使用預設 Windows 驗證方法，請選取 [由應用程式定義]。  
  
 **程式關閉模式**  
 選取 [啟動表單關閉時]\(預設)，來指定應用程式在設為啟動表單的表單關閉時結束 (即使已開啟其他表單也是一樣)。 選取 [最後一個表單關閉時]，來指定應用程式在最後一個表單關閉時或者明確呼叫 `My.Application.Exit` 或 `End` 陳述式時結束。  
  
 選取 [在明確關機時]，來指定應用程式在明確呼叫 `Shutdown` 時結束。  
  
 選取 [在最後一個視窗關閉時]，來指定應用程式在最後一個視窗關閉時或明確呼叫 `Shutdown` 時結束。 這是預設設定。  
  
 選取 [在主視窗關閉時]，來指定應用程式在主視窗關閉時或明確呼叫 `Shutdown` 時結束。  
  
 **啟動顯示畫面**  
 選取您想要用來當作啟動顯示畫面的表單。 您必須先前已使用表單或範本來建立啟動顯示畫面。 預設值為 [(無)]。  
  
 **檢視應用程式事件**  
 按一下此按鈕，以顯示您可用來撰寫應用程式架構事件 `Startup`、`Shutdown`、`UnhandledException`、`StartupNextInstance` 和 `NetworkAvailabilityChanged` 之事件的事件程式碼檔案。 您也可以覆寫特定應用程式架構方法。 例如，您可以覆寫 `OnInitialize` 來變更啟動顯示畫面的顯示行為。  
  
### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Windows Presentation Foundation (WPF) 應用程式的 Windows 應用程式架構屬性  
 專案是 Windows Presentation Foundation 應用程式時，[Windows 應用程式架構屬性] 區段中具有下列設定。 只有在選取 [啟用應用程式架構] 核取方塊時，才能使用這些選項。 此表格中所列的選項僅適用於 WPF 應用程式或 WPF 瀏覽器應用程式。 它們不適用於 WPF 使用者控制項或自訂控制項程式庫。  
  
 **程式關閉模式**  
 此屬性只適用於 Windows Presentation Foundation 應用程式。  
  
 選取 [在明確關機時]，來指定應用程式在明確呼叫 <xref:System.Windows.Application.Shutdown%2A> 時結束。  
  
 選取 [在最後一個視窗關閉時]，來指定應用程式在最後一個視窗關閉時或明確呼叫 <xref:System.Windows.Application.Shutdown%2A> 時結束。 這是預設設定。  
  
 選取 [在主視窗關閉時]，來指定應用程式在主視窗關閉時或明確呼叫 <xref:System.Windows.Application.Shutdown%2A> 時結束。  
  
 如需使用此設定的詳細資訊，請參閱 <xref:System.Windows.Application.Shutdown%2A>。  
  
 **編輯 XAML**  
 按一下此按鈕，以使用 XAML 編輯器開啟並修改應用程式定義檔案 (Application.xaml)。 按一下此按鈕時，會開啟應用程式定義節點上的 Application.xaml。 您可能必須編輯此檔案，才能執行特定工作 (例如定義資源)。 如果應用程式定義檔案不存在，則 [專案設計工具] 會建立一個應用程式定義檔案。  
  
 **檢視應用程式事件**  
 按一下此按鈕，以在程式碼編輯器中顯示 `Application` 部分類別檔案 (Application.xaml.vb)。 如果檔案不存在，則 [專案設計工具] 會建立一個具有適當類別名稱和命名空間的檔案。  
  
 特定應用程式狀態變更時 (例如，應用程式啟動或關機時)，<xref:System.Windows.Application> 物件會引發事件。 如需此類別所公開的完整事件清單，請參閱 <xref:System.Windows.Application>。 這些事件是在 `Application` 部分類別的使用者程式碼區段中處理。  
  
## <a name="see-also"></a>請參閱  
[管理應用程式屬性](../../ide/application-properties.md)[撰寫 Office 方案中的程式碼](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
