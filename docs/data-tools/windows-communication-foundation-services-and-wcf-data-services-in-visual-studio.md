---
title: Windows Communication Foundation 和 WCF Data Services
description: 探索 Windows Communication Foundation 在 Visual Studio 中 (WCF) 服務和 WCF Data Services，讓您可以建立分散式應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- VB
- CSharp
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: fb5ace269d7770d0e7d360734268d3e7adfda319
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866121"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務

Visual Studio 提供的工具可讓您使用 Windows Communication Foundation 的 (WCF) 和 WCF Data Services，這是用來建立分散式應用程式的 Microsoft 技術。 本主題提供 Visual Studio 觀點的服務簡介。 如需完整檔，請參閱 [WCF Data Services 4.5](/dotnet/framework/data/wcf/index)。

## <a name="what-is-wcf"></a>什麼是 WCF？

Windows Communication Foundation (WCF) 是統一的架構，可建立安全、可靠、交易和互通的分散式應用程式。 它取代了舊版的處理序間通訊技術，例如 .ASMX web 服務、.NET 遠端處理、企業服務 (DCOM) 和 MSMQ。 WCF 在統一的程式設計模型下，將所有這些技術的功能結合在一起。 這可簡化開發分散式應用程式的體驗。

### <a name="what-are-wcf-data-services"></a>什麼是 WCF Data Services

WCF Data Services 是開放式資料 (OData) 通訊協定標準的實作為。  WCF Data Services 可讓您將表格式資料公開為一組 REST Api，可讓您使用標準 HTTP 動詞命令（例如 GET、POST、PUT 或 DELETE）來傳回資料。 在伺服器端，WCF Data Services 被 [ASP.NET Web API](https://dotnet.microsoft.com/apps/aspnet/apis) 取代，以建立新的 OData 服務。 WCF Data Services 的用戶端程式庫會繼續是在 .net 應用程式中使用 OData 服務的理想選擇，從 Visual Studio (**Project**  >  **加入服務參考**) 。 如需詳細資訊，請參閱 [WCF Data Services 4.5](/dotnet/framework/data/wcf)。

### <a name="wcf-programming-model"></a>WCF 程式設計模型

WCF 程式設計模型是以兩個實體（WCF 服務和 WCF 用戶端）之間的通訊為基礎。 程式設計模型會封裝在 <xref:System.ServiceModel> .net 的命名空間中。

### <a name="wcf-service"></a>WCF 服務

WCF 服務是以定義服務與用戶端之間合約的介面為基礎。 它會以屬性標記 <xref:System.ServiceModel.ServiceContractAttribute> ，如下列程式碼所示：

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

您可以使用屬性來標記 WCF 服務，藉此定義它們所公開的函式或方法 <xref:System.ServiceModel.OperationContractAttribute> 。

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

此外，您可以藉由將複合類型標示為屬性，來公開序列化的資料 <xref:System.Runtime.Serialization.DataContractAttribute> 。 這樣就可以在用戶端中進行資料系結。

定義介面和其方法之後，會將其封裝在實介面的類別中。 單一 WCF 服務類別可以執行多個服務合約。

WCF 服務會透過所謂的 *端點* 來公開取用。 端點提供與服務通訊的唯一方法;您無法透過直接參考存取服務，就像使用其他類別一樣。

端點是由位址、系結和合約所組成。 位址會定義服務所在的位置;這可能是 URL、FTP 位址或網路或本機路徑。 系結會定義您與服務通訊的方式。 WCF 系結提供多用途的模型來指定通訊協定（例如 HTTP 或 FTP）、安全性機制（例如 Windows 驗證）或使用者名稱和密碼等等。 合約包含 WCF 服務類別所公開的作業。

單一 WCF 服務可以公開多個端點。 這可讓不同的用戶端以不同的方式與相同的服務通訊。 例如，銀行服務可能會為員工提供一個端點，並為外部客戶提供另一個端點，每個端點使用不同的位址、系結和/或合約。

### <a name="wcf-client"></a>WCF Client - WCF 用戶端

WCF 用戶端所包含的 *proxy* 可讓應用程式與 WCF 服務進行通訊，以及符合為服務定義之端點的端點。 Proxy 是在 *app.config* 檔案的用戶端上產生，並且包含服務所公開之類型和方法的相關資訊。 對於公開多個端點的服務，用戶端可以選取最符合其需求的服務，例如，透過 HTTP 進行通訊並使用 Windows 驗證。

建立 WCF 用戶端之後，您可以參考程式碼中的服務，就像處理任何其他物件一樣。 例如，若要呼叫稍 `GetData` 早所示的方法，您可以撰寫類似下面的程式碼：

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio 中的 WCF 工具

Visual Studio 提供可協助您建立 WCF 服務和 WCF 用戶端的工具。 如需示範工具的逐步解說，請參閱 [逐步解說：在 Windows Forms 中建立簡單的 WCF 服務](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)。

### <a name="create-and-test-wcf-services"></a>建立和測試 WCF 服務

您可以使用 WCF Visual Studio 範本作為基礎，快速建立您自己的服務。 然後，您可以使用 WCF 服務自動主機和 WCF 測試用戶端，來對服務進行 debug 錯和測試。 這些工具可一起提供快速且方便的偵錯工具，並不需要在早期階段認可至裝載模型。

#### <a name="wcf-templates"></a>WCF 範本

WCF Visual Studio 範本提供服務開發的基本類別結構。 [ **加入新專案** ] 對話方塊中提供數個 WCF 範本。 這包括 WCF 服務 lLibrary 專案、WCF 服務網站和 WCF 服務專案範本。

當您選取範本時，會針對服務合約、服務執行和服務設定新增檔案。 已新增所有必要的屬性，建立簡單的「Hello World」類型的服務，您不需要撰寫任何程式碼。 當然，您會想要新增程式碼來為您的真實世界服務提供函數和方法，但範本會提供基本的基礎。

若要深入瞭解 WCF 範本，請參閱 [wcf Visual Studio 範本](/dotnet/framework/wcf/wcf-vs-templates)。

#### <a name="wcf-service-host"></a>WCF 服務主機

當您針對 WCF 服務專案按下 **F5**) 啟動 Visual Studio 偵錯工具 (時，會自動啟動 Wcf 服務主機工具，以在本機裝載服務。 WCF 服務主機會列舉 WCF 服務專案中的服務、載入專案的設定，並為它找到的每個服務具現化主機。

使用 WCF 服務主機，您可以測試 WCF 服務，而不需要撰寫額外的程式碼，或在開發期間認可至特定的主機。

若要深入瞭解 WCF 服務主機，請參閱 [wcf 服務主機 ( # A0) ](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)。

#### <a name="wcf-test-client"></a>WCF 測試用戶端

WCF 測試用戶端工具可讓您輸入測試參數、將該輸入提交至 WCF 服務，以及查看服務傳回的回應。 當您將它與 WCF 服務主機結合時，它會提供便利的服務測試體驗。 在 *% ProgramFiles (x86) % \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* 資料夾中尋找工具。

當您按下 **F5** 以偵測 wcf 服務專案時，WCF 測試用戶端會開啟並顯示設定檔中定義的服務端點清單。 您可以測試參數並啟動服務，然後重複此程式以持續測試及驗證您的服務。

若要深入瞭解 WCF 測試用戶端，請參閱 [wcf 測試用戶端 ( # A0) ](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe)。

### <a name="accessing-wcf-services-in-visual-studio"></a>存取 Visual Studio 中的 WCF 服務

Visual Studio 簡化了建立 WCF 用戶端的工作，為您使用 [ **加入服務參考** ] 對話方塊加入的服務自動產生 proxy 和端點。 所有必要的設定資訊都會新增至 *app.config* 檔案中。 大部分的情況下，您只需要將服務具現化，才能使用它。

[ **加入服務參考** ] 對話方塊可讓您輸入服務的位址，或搜尋解決方案中定義的服務。 對話方塊會傳回服務清單以及這些服務所提供的作業。 它也可讓您定義您將在程式碼中參考服務的命名空間。

[ **設定服務參考** ] 對話方塊可讓您自訂服務的設定。 您可以變更服務的位址、指定存取層級、非同步行為和訊息合約類型，以及設定類型重複使用。

## <a name="how-to-select-a-service-endpoint"></a>如何：選取服務端點

某些 Windows Communication Foundation (WCF) 服務會公開多個端點，以供用戶端與服務通訊。 例如，服務可能會公開一個使用 HTTP 系結的端點、使用者名稱和密碼安全性，以及使用 FTP 和 Windows 驗證的第二個端點。 第一個端點可能會由從防火牆外部存取服務的應用程式使用，而第二個端點則可能用於內部網路。

在這種情況下，您可以將 `endpointConfigurationName` 做為參數，指定給服務參考的函式。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>選取服務端點

1. 在 **方案總管** 中，以滑鼠右鍵按一下專案節點，然後選擇 [ **加入服務參考**]，以新增 WCF 服務的參考。

2. 在 [程式碼編輯器] 中，加入服務參考的函式：

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > 將 *ServiceReference* 取代為服務參考的命名空間，並以服務的名稱取代 *Service1Client* 。

3. 包含此函式之多載的 IntelliSense 清單隨即顯示。 選取多載 `endpointConfigurationName As String` 。

4. 在多載之後，輸入 `=` *ConfigurationName*，其中 *ConfigurationName* 是您要使用之端點的名稱。

    > [!NOTE]
    > 如果您不知道可用端點的名稱，您可以在 *app.config* 檔案中找到它們。

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>尋找 WCF 服務的可用端點

1. 在 **方案總管** 中，以滑鼠右鍵按一下包含服務參考之專案的 **app.config** 檔案，然後按一下 [ **開啟**]。 檔案會出現在程式碼編輯器中。

2. `<Client>`在檔案中搜尋標記。

3. 在標記下方搜尋開頭為的 `<Client>` 標記 `<Endpoint>` 。

     如果服務參考提供多個端點，則會有兩個或多個 `<Endpoint` 標記。

4. 在 `<EndPoint>` 標記中，您會發現 `name="` *SomeService* `"` 參數 (其中 *SomeService* 代表端點名稱) 。 這是可傳遞給服務參考的函式多載之端點的名稱 `endpointConfigurationName As String` 。

## <a name="how-to-call-a-service-method-asynchronously"></a>如何：以非同步方式呼叫服務方法

Windows Communication Foundation 中 (WCF) 服務的大部分方法，都可以同步或非同步方式呼叫。 以非同步方式呼叫方法，可讓您的應用程式在呼叫方法時，仍可繼續運作，但它會在慢速連線上運作。

根據預設，將服務參考加入至專案時，會將它設定為以同步方式呼叫方法。 您可以藉由變更 [ **設定服務參考** ] 對話方塊中的設定，將行為變更為以非同步方式呼叫方法。

> [!NOTE]
> 此選項是以每個服務為基礎來設定。 如果以非同步方式呼叫服務的一個方法，則所有方法都必須以非同步方式呼叫。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>以非同步方式呼叫服務方法

1. 在 **方案總管** 中，選取 [服務參考]。

2. 在 [ **專案** ] 功能表上，按一下 [ **設定服務參考**]。

3. 在 [ **設定服務參考** ] 對話方塊中，選取 [ **產生非同步作業** ] 核取方塊。

## <a name="how-to-bind-data-returned-by-a-service"></a>如何：系結服務所傳回的資料

您可以將 Windows Communication Foundation (WCF) 服務所傳回的資料系結至控制項，就像您可以將任何其他資料來源系結至控制項一樣。 當您加入 WCF 服務的參考時，如果服務包含傳回資料的複合類型，則會自動將它們加入至 [ **資料來源** ] 視窗。

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>將控制項系結至 WCF 服務所傳回的單一資料欄位

1. 按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。

   隨即出現 [資料來源] 視窗。

2. 在 [ **資料來源** ] 視窗中，展開服務參考的節點。 服務顯示所傳回的任何複合類型。

3. 展開型別的節點。 該類型的資料欄位隨即出現。

4. 選取欄位，然後按一下下拉箭號，即可顯示該資料類型可用的控制項清單。

5. 按一下您要系結之控制項的類型。

6. 將欄位拖曳到表單上。 控制項會連同元件和元件一起加入表單中 <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> 。

7. 針對您想要系結的任何其他欄位，重複步驟4到6。

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>將控制項系結至 WCF 服務所傳回的複合類型

1. 在 [ **資料** ] 功能表上，選取 [ **顯示資料來源**]。 隨即出現 [資料來源] 視窗。

2. 在 [ **資料來源** ] 視窗中，展開服務參考的節點。 服務顯示所傳回的任何複合類型。

3. 選取類型的節點，然後按一下下拉式箭號以顯示可用選項的清單。

4. 按一下 [ **DataGridView** ]，即可在方格或 **詳細** 資料中顯示資料，以在個別控制項中顯示資料。

5. 將節點拖曳至表單上。 系統會將控制項加入至表單，連同 <xref:System.Windows.Forms.BindingSource> 元件和 <xref:System.Windows.Forms.BindingNavigator> 元件。

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>如何：設定服務以重複使用現有的類型

將服務參考加入至專案時，在服務中定義的任何類型都會在本機專案中產生。 在許多情況下，當服務使用常見的 .NET 類型或在共用程式庫中定義類型時，這會建立重複的類型。

為了避免這個問題，預設會共用參考元件中的類型。 如果您想要停用一或多個元件的類型共用，您可以在 [ **設定服務參考** ] 對話方塊中進行。

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>停用單一元件中的類型共用

1. 在 **方案總管** 中，選取 [服務參考]。

2. 在 [ **專案** ] 功能表上，按一下 [ **設定服務參考**]。

3. 在 [ **設定服務參考** ] 對話方塊中，選取 [ **重複使用指定的參考元件中的類型**]。

4. 針對您要啟用類型共用的每個元件，選取其核取方塊。 若要停用元件的類型共用，請將核取方塊保留為已清除。

### <a name="to-disable-type-sharing-in-all-assemblies"></a>停用所有元件中的類型共用

1. 在 **方案總管** 中，選取 [服務參考]。

2. 在 [ **專案** ] 功能表上，按一下 [ **設定服務參考**]。

3. 在 [ **設定服務參考** ] 對話方塊中，清除 [ **重複使用參考元件中的類型** ] 核取方塊。

## <a name="related-topics"></a>相關主題

| 標題 | 描述 |
| - | - |
| [逐步解說：在 Windows Forms 中建立簡單的 WCF 服務](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | 提供在 Visual Studio 中建立和使用 WCF 服務的逐步示範。 |
| [逐步解說︰使用 WPF 和 Entity Framework 建立 WCF 資料服務](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | 提供如何建立和使用 Visual Studio 中之 WCF Data Services 的逐步示範。 |
| [使用 WCF 開發工具](/dotnet/framework/wcf/using-the-wcf-development-tools) | 討論如何在 Visual Studio 中建立及測試 WCF 服務。 |
| | [如何：加入、更新或移除 WCF 資料服務參考](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [針對服務參考進行疑難排解](../data-tools/troubleshooting-service-references.md) | 提供一些可能會在服務參考中發生的常見錯誤，以及如何防止這些錯誤。 |
| [WCF 服務的調試](../debugger/debugging-wcf-services.md) | 描述當您在調試 WCF 服務時，可能會遇到的常見調試問題和技巧。 |
| [逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | 提供用於建立具類型資料集以及將 TableAdapter 和資料集程式碼分成多個專案的逐步指示。 |
| [[設定服務參考] 對話方塊](../data-tools/configure-service-reference-dialog-box.md) | 描述 [ **設定服務參考** ] 對話方塊的使用者介面元素。 |

## <a name="reference"></a>參考

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
