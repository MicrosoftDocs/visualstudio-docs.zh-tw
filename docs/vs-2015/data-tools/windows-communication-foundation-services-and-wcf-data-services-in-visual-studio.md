---
title: Windows Communication Foundation 服務和 WCF 資料服務
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e988c8818cdee756310b73d0d214deda43226f2b
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850219"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 提供使用 Windows Communication Foundation （WCF）和 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]的工具，這是用來建立分散式應用程式的 Microsoft 技術。 本主題提供 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 觀點的服務簡介。 如需完整的檔，請參閱[WCF Data Services 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)。

## <a name="what-is-wcf"></a>什麼是 WCF？
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 是統一的架構，可建立安全、可靠、交易和互通的分散式應用程式。 它會取代舊版的處理序間通訊技術，例如，.ASMX Web 服務、.NET 遠端處理、企業服務（DCOM）和 MSMQ。 WCF 將所有這些技術的功能整合在統一的程式設計模型下。 這可簡化開發分散式應用程式的體驗。

#### <a name="what-are-wcf-data-services"></a>WCF Data Services 的內容
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 是開放式資料（OData）通訊協定標準的執行。  WCF Data Services 可讓您將表格式資料公開為一組 REST Api，可讓您使用標準 HTTP 動詞命令（例如 GET、POST、PUT 或 DELETE）來傳回資料。 在伺服器端上，WCF Data Services 由[ASP.NET Web API](https://dotnet.microsoft.com/apps/aspnet/apis)取代，以建立新的 OData 服務。 WCF Data Services 用戶端程式庫會持續成為在 .NET 應用程式中使用 OData 服務的最佳選擇，Visual Studio **（ &#124; Project 加入服務參考**）。 如需詳細資訊，請參閱 [WCF Data Services 4.5](https://msdn.microsoft.com/library/cc668792.aspx)。

### <a name="wcf-programming-model"></a>WCF 程式設計模型
 WCF 程式設計模型是以兩個實體之間的通訊為基礎： WCF 服務和 WCF 用戶端。 程式設計模型會封裝在 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]的 <xref:System.ServiceModel> 命名空間中。

#### <a name="wcf-service"></a>WCF 服務
 WCF 服務是以定義服務與用戶端之間合約的介面為基礎。 它會標示 <xref:System.ServiceModel.ServiceContractAttribute> 屬性，如下列程式碼所示：

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 藉由使用 <xref:System.ServiceModel.OperationContractAttribute> 屬性來標記 WCF 服務所公開的函式或方法，即可加以定義。 此外，您可以使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性來標記複合類型，藉以公開序列化的資料。 這會啟用用戶端中的資料系結。

 定義介面及其方法之後，會將其封裝在執行介面的類別中。 單一 WCF 服務類別可以執行多個服務合約。

 WCF 服務會透過所謂的*端點*來公開取用。 端點提供與服務通訊的唯一方式;您無法透過直接參考存取服務，就像使用其他類別一樣。

 端點是由位址、系結和合約所組成。 位址會定義服務的所在位置;這可能是 URL、FTP 位址或網路或本機路徑。 「系結」（binding）定義與服務通訊的方式。 WCF 系結提供了一種用來指定通訊協定（例如 HTTP 或 FTP）、安全性機制（例如 Windows 驗證或使用者名稱和密碼等）的多用途模型。 合約包含 WCF 服務類別所公開的作業。

 單一 WCF 服務可以公開多個端點。 這可讓不同的用戶端以不同的方式與相同的服務通訊。 例如，銀行服務可能為員工提供一個端點，另一個用於外部客戶，分別使用不同的位址、系結和/或合約。

#### <a name="wcf-client"></a>WCF 用戶端
 WCF 用戶端是由可讓應用程式與 WCF 服務通訊的*proxy* ，以及符合為服務定義之端點的端點所組成。 Proxy 會在 app.config 檔案的用戶端上產生，並包含服務所公開之類型和方法的相關資訊。 對於公開多個端點的服務，用戶端可以選取最符合其需求的服務，例如，透過 HTTP 進行通訊並使用 Windows 驗證。

 建立 WCF 用戶端之後，您可以參考程式碼中的服務，就像任何其他物件一樣。 例如，若要呼叫稍早所示的 `GetData` 方法，您可以撰寫類似下面的程式碼：

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio 中的 WCF 工具
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供的工具可協助您建立 WCF 服務和 WCF 用戶端。 如需示範工具的逐步解說，請參閱[逐步解說：在 Windows Forms 中建立簡單的 WCF 服務](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)。

### <a name="creating-and-testing-wcf-services"></a>建立和測試 WCF 服務
 您可以使用 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 範本作為基礎，以快速建立您自己的服務。 接著，您可以使用 WCF 服務自動裝載和 WCF 測試用戶端來進行服務的調試和測試。 這些工具一起提供快速且方便的偵錯工具和測試週期，並且不需要在早期階段認可至裝載模型。

#### <a name="wcf-templates"></a>WCF 範本
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 範本提供服務開發的基本類別結構。 [**加入新的專案**] 對話方塊中提供數個 WCF 範本。 其中包括 WCF 服務程式庫專案、WCF 服務網站和 WCF 服務專案範本。

 當您選取範本時，會針對服務合約、服務執行和服務設定加入檔案。 所有必要的屬性都已經加入、建立簡單的「Hello World」類型的服務，而且您不需要撰寫任何程式碼。 當然，您會想要新增程式碼來為您的真實世界服務提供函式和方法，但範本會提供基本的基礎。

 若要深入瞭解 WCF 範本，請參閱[wcf Visual Studio 範本](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f)。

#### <a name="wcf-service-host"></a>WCF 服務主機
 當您啟動 WCF 服務專案的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯工具（按 F5）時，WCF 服務主機工具會自動啟動以在本機裝載服務。 WCF 服務主機會列舉 WCF 服務專案中的服務、載入專案的設定，以及為它找到的每個服務具現化主機。

 藉由使用 WCF 服務主機，您可以測試 WCF 服務，而不需要在開發期間撰寫額外的程式碼或認可特定主機。

 若要深入瞭解 WCF 服務主機，請參閱[Wcf 服務主機（WcfSvcHost .exe）](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e)。

#### <a name="wcf-test-client"></a>WCF 測試用戶端
 [WCF 測試用戶端] 工具可讓您輸入測試參數、將該輸入提交至 WCF 服務，以及查看服務傳回的回應。 當您將它與 WCF 服務主機結合時，它可提供便利的服務測試體驗。 您可以在 \Common7\IDE 資料夾中找到此工具，這是安裝在 C 磁片磁碟機中的 Visual Studio 2015： **C:\Program Files （x86） \Microsoft Visual Studio 14.0 \ Common7\IDE\\** 。

 當您按 F5 來進行 WCF 服務專案的偵錯工具時，WCF 測試用戶端會開啟並顯示在設定檔案中定義的服務端點清單。 您可以測試參數並啟動服務，並重複此程式來持續測試及驗證您的服務。

 若要深入瞭解 WCF 測試用戶端，請參閱[Wcf 測試用戶端（WcfTestClient .exe）](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7)。

### <a name="accessing-wcf-services-in-visual-studio"></a>存取 Visual Studio 中的 WCF 服務
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 簡化了建立 WCF 用戶端的工作，並自動為您使用 [**加入服務參考**] 對話方塊新增的服務產生 proxy 和端點。 所有必要的設定資訊都會新增至 app.config 檔案。 在大部分的情況下，您只需要具現化服務，才能使用它。

 [**加入服務參考**] 對話方塊可讓您輸入服務的位址，或搜尋在解決方案中定義的服務。 對話方塊會傳回服務的清單，以及這些服務所提供的作業。 它也可讓您定義要在程式碼中用來參考服務的命名空間。

 [**設定服務參考**] 對話方塊可讓您自訂服務的設定。 您可以變更服務的位址、指定存取層級、非同步行為和訊息合約類型，以及設定類型重複使用。

## <a name="how-to-select-a-service-endpoint"></a>如何：選取服務端點
 某些 Windows Communication Foundation （WCF）服務會公開多個端點，用戶端可以透過此服務進行通訊。 例如，服務可能會公開一個使用 HTTP 系結的端點，以及使用 FTP 和 Windows 驗證的使用者名稱/密碼安全性和第二個端點。 從防火牆外部存取服務的應用程式可能會使用第一個端點，而第二個則可能用於內部網路。

 在這種情況下，您可以將 `endpointConfigurationName` 指定為服務參考之函式的參數。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>選取服務端點

1. 在方案總管中以滑鼠右鍵按一下專案節點，然後選擇 [**加入服務參考**]，以加入 WCF 服務的參考

2. 在 [程式碼編輯器] 中，加入服務參考的函式：

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > 將*ServiceReference*取代為服務參考的命名空間，並將*Service1Client*取代為服務的名稱。

3. IntelliSense 清單會與此函式的多載一起顯示。 選取 `endpointConfigurationName As String` 多載。

4. 在多載之後，輸入 `=` *ConfigurationName*，其中*ConfigurationName*是您要使用之端點的名稱。

    > [!NOTE]
    > 如果您不知道可用端點的名稱，您可以在 app.config 檔案中找到它們。

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>尋找 WCF 服務的可用端點

1. 在**方案總管**中，以滑鼠右鍵按一下包含服務參考之專案的 app.config 檔案，然後按一下 [**開啟**]。 檔案會出現在程式碼編輯器中。

2. 搜尋檔案中的 `<Client>` 標記。

3. 在 `<Client>` 標籤下方搜尋 `<Endpoint>`開頭的標記。

     如果服務參考提供多個端點，則會有兩個以上的 `<Endpoint` 標記。

4. 在 `<EndPoint>` 標記內，您會發現 `name="`*SomeService*`"` 參數（其中*SomeService*代表端點名稱）。 這是可傳遞給服務參考之函式的 `endpointConfigurationName As String` 多載的端點名稱。

## <a name="how-to-call-a-service-method-asynchronously"></a>如何：以非同步方式呼叫服務方法
 Windows Communication Foundation （WCF）服務中的大部分方法可能會以同步或非同步方式呼叫。 以非同步方式呼叫方法，可讓您的應用程式在呼叫速度較慢的連接時，仍可繼續運作。

 根據預設，當服務參考加入至專案時，它會設定為同步呼叫方法。 您可以藉由變更 [**設定服務參考**] 對話方塊中的設定，將行為變更為以非同步方式呼叫方法。

> [!NOTE]
> 此選項是根據每個服務來設定。 如果服務的其中一個方法是以非同步方式呼叫，所有方法都必須以非同步方式呼叫。

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>若要以非同步方式呼叫服務方法

1. 在 **方案總管**中，選取 服務參考。

2. 在 [**專案**] 功能表上，按一下 [**設定服務參考**]。

3. 在 [**設定服務參考**] 對話方塊中，選取 [**產生非同步作業**] 核取方塊。

## <a name="how-to-bind-data-returned-by-a-service"></a>如何：系結服務所傳回的資料
 您可以將 Windows Communication Foundation （WCF）服務所傳回的資料系結至控制項，就像您可以將任何其他資料來源系結至控制項一樣。 當您將參考加入至 WCF 服務時，如果服務包含會傳回資料的複合類型，則會自動將其加入至 [**資料來源**] 視窗。

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>若要將控制項系結至 WCF 服務所傳回的單一資料欄位

1. 按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。 [**資料來源**] 視窗隨即出現。

2. 在 [**資料來源**] 視窗中，展開服務參考的節點。 將會顯示服務所傳回的任何複合類型。

3. 展開類型的節點。 將會顯示該類型的資料欄位。

4. 選取欄位，然後按一下下拉箭號，即可顯示資料類型可用的控制項清單。

5. 按一下您要系結的控制項類型。

6. 將欄位拖曳至表單上。 控制項將會與 <xref:System.Windows.Forms.BindingSource> 元件和 <xref:System.Windows.Forms.BindingNavigator> 元件一起加入表單中。

7. 針對您想要系結的任何其他欄位，重複步驟4到6。

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>若要將控制項系結至 WCF 服務所傳回的複合類型

1. 在 [**資料**] 功能表上，選取 [**顯示資料來源**]。 [**資料來源**] 視窗隨即出現。

2. 在 [**資料來源**] 視窗中，展開服務參考的節點。 將會顯示服務所傳回的任何複合類型。

3. 選取類型的節點，然後按一下下拉箭號，以顯示可用的選項清單。

4. 按一下 [ **DataGridView** ]，將資料顯示在方格或**詳細**資料中，以在個別控制項中顯示資料。

5. 將節點拖曳至表單上。 控制項會與 <xref:System.Windows.Forms.BindingSource> 元件和 <xref:System.Windows.Forms.BindingNavigator> 元件一起加入表單中。

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>如何：設定服務以重複使用現有的類型
 將服務參考加入至專案時，會在本機專案中產生服務中定義的任何類型。 在許多情況下，當服務使用通用 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 類型，或在共用程式庫中定義類型時，這會建立重複的類型。

 為了避免這個問題，預設會共用參考元件中的類型。 如果您想要停用一個或多個元件的類型共用，您可以在 [**設定服務參考**] 對話方塊中執行此動作。

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>停用單一元件中的類型共用

1. 在 **方案總管**中，選取 服務參考。

2. 在 [**專案**] 功能表上，按一下 [**設定服務參考**]。

3. 在 [**設定服務參考**] 對話方塊中，選取 [**重複使用指定的參考元件中的類型**]。

4. 針對您要啟用類型共用的每個元件，選取核取方塊。 若要停用元件的類型共用，請將此核取方塊保留為已清除。

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>停用所有元件中的類型共用

1. 在 **方案總管**中，選取 服務參考。

2. 在 [**專案**] 功能表上，按一下 [**設定服務參考**]。

3. 在 [**設定服務參考**] 對話方塊中，清除 [**重複使用參考元件中的類型**] 核取方塊。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[逐步解說：在 Windows Forms 中建立簡單的 WCF 服務](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|逐步示範如何在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中建立和使用 WCF 服務。|
|[逐步解說︰使用 WPF 和 Entity Framework 建立 WCF 資料服務](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|提供逐步示範如何在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中建立和使用 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]。|
|[使用 WCF 開發工具](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|討論如何在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中建立和測試 WCF 服務。|
|[如何：加入、更新或移除服務參考](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|描述如何新增、更新或移除專案中的 WCF 服務。|
|[如何：新增、更新或移除 WCF 資料服務參考](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|討論如何參考和使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中的 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]。|
|[服務參考的疑難排解](../data-tools/troubleshooting-service-references.md)|提供服務參考時可能發生的一些常見錯誤，以及如何預防它們。|
|[偵錯 WCF 服務](../debugger/debugging-wcf-services.md)|說明您在對 WCF 服務進行調試時可能會遇到的常見調試問題和技巧。|
|[Windows Communication Foundation Authentication 服務總覽](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|描述如何使用 WCF 來提供網站的角色服務。|
|[逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|提供用於建立具類型資料集以及將 TableAdapter 和資料集程式碼分成多個專案的逐步指示。|
|[設定服務參考對話方塊](../data-tools/configure-service-reference-dialog-box.md)|描述 [**設定服務參考**] 對話方塊的使用者介面元素。|

## <a name="reference"></a>參考資料
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>請參閱
 [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
