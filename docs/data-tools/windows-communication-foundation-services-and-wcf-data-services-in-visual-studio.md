---
title: Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3f3a558e91496006b0d4750492f0ec9abce7333f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務
Visual Studio 提供工具使用與 Windows Communication Foundation (WCF) 和[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]，Microsoft 技術，用於建立分散式應用程式。 本主題提供簡介服務從[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]檢視方塊。 如需完整的文件，請參閱[WCF 資料服務 4.5](/dotnet/framework/data/wcf/index)。

## <a name="what-is-wcf"></a>WCF 是什麼？
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] 是一個整合的架構，建立安全、 可靠、 交易，以及可互通的分散式應用程式。 它會取代舊的處理序間通訊技術，例如 ASMX Web 服務、.NET 遠端處理、 企業服務 (DCOM) 及 MSMQ。 WCF 結合了統一的程式設計模式下的所有這些技術的功能。 這樣可簡化開發分散式應用程式的體驗。

#### <a name="what-are-wcf-data-services"></a>WCF 資料服務有哪些？
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 是標準的開放式資料 (OData) 通訊協定的實作。  WCF 資料服務可讓您將表格式資料公開為一組 REST Api，可讓您傳回資料，例如使用標準 HTTP 動詞 GET、 POST、 PUT 或 DELETE。 在伺服器端，WCF Data Services 正在取代的[ASP.NET Web API](http://www.asp.net/web-api)建立新的 OData 服務。 WCF 資料服務用戶端程式庫將繼續使用.NET 應用程式，從 Visual Studio 中的 OData 服務的理想選擇 (**專案&#124;加入服務參考**)。 如需詳細資訊，請參閱[WCF 資料服務 4.5](http://go.microsoft.com/fwlink/?LinkID=119952)。

### <a name="wcf-programming-model"></a>WCF 程式設計模型
 WCF 程式設計模型根據兩個實體之間的通訊： WCF 服務和 WCF 用戶端。 程式設計模型會封裝在<xref:System.ServiceModel>命名空間中的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]。

#### <a name="wcf-service"></a>WCF 服務
 WCF 服務根據這個介面會定義服務與用戶端之間的合約。 它以標示<xref:System.ServiceModel.ServiceContractAttribute>屬性，如下列程式碼所示：

 [!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

 [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

 您定義函數或方法來標記它們與 WCF 服務所公開的<xref:System.ServiceModel.OperationContractAttribute>屬性。 此外，您可以公開序列化的資料標記與一種複合類型<xref:System.Runtime.Serialization.DataContractAttribute>屬性。 這可讓用戶端中的資料繫結。

 介面和其方法定義之後，就會封裝實作介面的類別中。 單一 WCF 服務類別可實作多個服務合約。

 WCF 服務會公開透過耗用量稱為*端點*。 端點可提供與服務通訊的唯一方法與其他類別一樣，您無法存取服務透過直接參考。

 端點是由位址、 繫結及合約所組成。 位址會定義服務所在的位置。這可能是 URL、 FTP 位址，或網路或本機路徑。 繫結會定義您的服務通訊的方式。 WCF 繫結提供靈活的模型指定的通訊協定，例如 HTTP 或 FTP，例如 Windows 驗證或使用者名稱和密碼的安全性機制及其他更多。 合約包含由 WCF 服務類別公開的作業。

 多個端點可以公開為單一 WCF 服務。 這可讓不同的用戶端不同的方式與在相同的服務通訊。 例如，銀行服務可能會提供一個端點的員工，而另一個外部客戶，每個使用不同的位址、 繫結，及/或合約。

#### <a name="wcf-client"></a>WCF 用戶端
 WCF 用戶端組成*proxy* ，可讓 WCF 服務，與通訊的應用程式和服務定義符合端點的端點。 Proxy 會在用戶端的 app.config 檔中產生，並包含的類型和服務所公開的方法的相關資訊。 公開多個端點的服務，用戶端可以選取其中一個最符合其需求，例如，透過 HTTP 通訊，並使用 Windows 驗證。

 已建立 WCF 用戶端之後，您服務中參考您的程式碼就像任何其他物件一樣。 例如，若要呼叫`GetData`方法之前，顯示您要撰寫程式碼，如下所示：

 [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio 中的 WCF 工具
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供可協助您建立 WCF 服務和 WCF 用戶端工具。 如需示範這些工具的逐步解說，請參閱[逐步解說： 在 Windows Form 中建立簡單的 WCF 服務](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)。

### <a name="creating-and-testing-wcf-services"></a>建立及測試 WCF 服務
 您可以使用 WCF[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]做為基礎，快速建立您自己的服務範本。 您可以接著使用 WCF 服務自動主機以及 WCF 測試用戶端偵錯及測試服務。 這些工具一起提供快速且方便偵錯和測試週期，以及排除在早期階段認可裝載模型的需求。

#### <a name="wcf-templates"></a>WCF 範本
 WCF[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]範本提供服務開發的基本類別結構。 數個 WCF 範本位於**加入新的專案** 對話方塊。 這些包括 WCF 服務庫專案中，WCF 服務網站和 WCF 服務項目範本。

 當您選取範本時，檔案會新增為服務合約、 服務實作，並與服務組態。 已加入所有必要的屬性，建立簡單"Hello World"類型的服務，而且您不需要撰寫任何程式碼。 您當然，會想要將程式碼加入提供函式和方法，為您真實世界的服務，但範本會提供基本的基礎。

 若要深入了解 WCF 範本，請參閱[WCF Visual Studio 範本](/dotnet/framework/wcf/wcf-vs-templates)。

#### <a name="wcf-service-host"></a>WCF 服務主機
 當您啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]偵錯工具 （可以按 f5 鍵） 的 WCF 服務專案中，工具會自動啟動來裝載在本機服務的 WCF 服務主機。 WCF 服務主機會列舉 WCF 服務專案中的服務、 載入專案的設定，並具現化每個服務所找到的主機。

 使用 WCF 服務主機，您可以測試 WCF 服務，而不需要撰寫額外的程式碼或認可特定主機在開發期間。

 若要深入了解 WCF 服務主機，請參閱[WCF 服務主機 (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)。

#### <a name="wcf-test-client"></a>WCF 測試用戶端
 WCF 測試用戶端工具可讓您輸入測試參數、 將該 WCF 服務，輸入送出，並檢視服務傳回的回應。 它提供便利的服務測試經驗，當您將其與 WCF 服務主機。 \Common7\IDE 資料夾中，Visual Studio 2015 安裝在磁碟機 c： 以下是可以找到這個工具： **C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\\**。

 當您按 F5 以偵錯 WCF 服務專案時，WCF 測試用戶端就會開啟，並顯示組態檔中定義的服務端點的清單。 您可以測試參數並啟動服務，並重複此程序以持續測試及驗證您的服務。

 若要深入了解 WCF 測試用戶端，請參閱[WCF 測試用戶端 (WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe)。

### <a name="accessing-wcf-services-in-visual-studio"></a>存取 Visual Studio 中的 WCF 服務
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可簡化建立 WCF 用戶端，會自動產生 proxy 和您使用新增的服務端點的工作**加入服務參考** 對話方塊。 所有必要的組態資訊會加入至 app.config 檔案。 大部分的情況下，您必須先執行所有是具現化服務才能使用它。

 **加入服務參考** 對話方塊可讓您輸入服務的位址，或搜尋您的方案中定義的服務。 對話方塊是傳回服務與這些服務所提供的作業的清單。 它也可讓您定義將參照的服務程式碼中的命名空間。

 **設定服務參考** 對話方塊可讓您自訂服務的組態。 您可以變更服務的位址、 指定存取層級、 非同步的行為，以及訊息合約型別，並設定型別重複使用。

## <a name="how-to-select-a-service-endpoint"></a>如何： 選取服務端點
有些 Windows Communication Foundation (WCF) 服務會公開透過此用戶端可能與服務通訊的多個端點。 例如，服務可能會公開一個端點使用 HTTP 繫結和使用者名稱 / 密碼安全性和使用 FTP 和 Windows 驗證的第二個端點。 存取服務的防火牆，外部的應用程式可能使用的第一個端點，而第二個可能會用在內部網路上。

在此情況下，您可以指定`endpointConfigurationName`做為服務參考的建構函式的參數。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-select-a-service-endpoint"></a>若要選取的服務端點

1.  加入 WCF 服務的參考，以滑鼠右鍵按一下方案總管 中的專案節點，然後選擇**加入服務參考**。

2.  在程式碼編輯器中，加入服務參考的建構函式：

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    >  取代*ServiceReference*服務參考] 和 [取代的命名空間與*Service1Client*與服務的名稱。

3.  多載建構函式會顯示 IntelliSense 清單。 選取`endpointConfigurationName As String`多載。

4.  下列多載中，輸入`=` *ConfigurationName*，其中*ConfigurationName*是您想要使用的端點名稱。

    > [!NOTE]
    >  如果您不知道可用的端點名稱，您可以在 app.config 檔案中找到它們。

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>若要尋找可用的端點的 WCF 服務

1.  在**方案總管 中**，以滑鼠右鍵按一下包含該服務參考的專案的 app.config 檔案，然後按一下**開啟**。 檔案會出現在程式碼編輯器。

2.  搜尋`<Client>`檔案中的標記。

3.  搜尋下`<Client>`標記開頭的標記`<Endpoint>`。

     如果服務參考會提供多個端點，會有兩個或多個`<Endpoint`標記。

4.  內部`<EndPoint>`標記，您會發現`name="` *SomeService* `"`參數 (其中*SomeService*代表端點名稱)。 這是可以傳遞至端點的名稱`endpointConfigurationName As String`的服務參考的建構函式多載。

## <a name="how-to-call-a-service-method-asynchronously"></a>如何： 以非同步方式呼叫服務方法
Windows Communication Foundation (WCF) 服務中的大部分方法可以同步或非同步方式呼叫。 以非同步方式呼叫的方法可讓您的應用程式繼續運作，而其運作方式連線速度很慢時，會呼叫方法。

根據預設，服務參考加入至專案時它被設定為以同步方式呼叫方法。 您可以變更來呼叫方法以非同步方式中變更行為**設定服務參考** 對話方塊。

> [!NOTE]
>  設定這個選項是以個別服務為基礎。 如果以非同步方式呼叫服務的一個方法，必須以非同步方式呼叫所有方法。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>若要以非同步方式呼叫服務方法

1.  在**方案總管] 中**，選取 [服務參考。

2.  在**專案**功能表上，按一下 **設定服務參考**。

3.  在**設定服務參考**對話方塊中，選取**產生非同步作業**核取方塊。

## <a name="how-to-bind-data-returned-by-a-service"></a>如何： 將服務所傳回的資料繫結
您可以就像您可以將任何其他資料來源繫結至控制項，Windows Communication Foundation (WCF) 服務所傳回至控制項的資料繫結。 當您新增到 WCF 服務的參考，如果服務包含傳回資料的複合類型時，使用者會自動新增**資料來源**視窗。

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>將控制項繫結至 WCF 服務所傳回的單一資料欄位

1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。 **資料來源**視窗會出現。

2.  在**資料來源**視窗中，展開 [服務參考] 節點。 將會顯示任何複合服務所傳回的型別。

3.  展開的節點類型。 將顯示該類型的資料欄位。

4.  選取的欄位，然後按一下下拉箭號以顯示可用於資料類型的控制項的清單。

5.  按一下您想要繫結至控制項的類型。

6.  將欄位拖曳到表單上。 控制項將會加入至與搭配表單<xref:System.Windows.Forms.BindingSource>元件和<xref:System.Windows.Forms.BindingNavigator>元件。

7.  重複步驟 4，6，對所有其他欄位，但您想要繫結。

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>將控制項繫結至 WCF 服務所傳回的複合類型

1.  在**資料**功能表上，選取**顯示資料來源**。 **資料來源**視窗會出現。

2.  在**資料來源**視窗中，展開 [服務參考] 節點。 將會顯示任何複合服務所傳回的型別。

3.  選取類型節點，然後按一下下拉箭號以顯示可用的選項清單。

4.  按一下  **DataGridView**在方格中顯示資料或**詳細資料**個別控制項中顯示資料。

5.  將節點拖曳至表單。 會將控制項加入至表單，並搭配<xref:System.Windows.Forms.BindingSource>元件和<xref:System.Windows.Forms.BindingNavigator>元件。

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>如何： 將服務設定為重複使用現有的型別
當服務參考加入至專案時，本機專案會產生任何服務中所定義的型別。 在許多情況下，這會建立重複的型別時，服務會使用一般[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]型別或型別共用文件庫中已定義。

若要避免這個問題，預設被共用參考的組件中的型別。 如果您想要停用類型共用的一或多個組件，您可以執行這個動作**設定服務參考** 對話方塊。

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>若要停用的單一組件中的類型共用

1.  在**方案總管] 中**，選取 [服務參考。

2.  在**專案**功能表上，按一下 **設定服務參考**。

3.  在**設定服務參考**對話方塊中，選取**重複使用指定參考的組件中的型別**。

4.  選取核取方塊，每一個您要啟用類型共用的組件。 若要停用類型共用之組件，請不要核取方塊。

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>若要停用所有組件中的類型共用

1.  在**方案總管] 中**，選取 [服務參考。

2.  在**專案**功能表上，按一下 **設定服務參考**。

3.  在**設定服務參考**對話方塊中，清除**重複使用參考組件中的型別**核取方塊。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[逐步解說：在 Windows Forms 中建立簡單的 WCF 服務](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|提供建立和使用中的 WCF 服務的逐步示範[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|
|[逐步解說︰使用 WPF 和 Entity Framework 建立 WCF 資料服務](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|提供的逐步示範如何建立及使用[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|
|[使用 WCF 開發工具](/dotnet/framework/wcf/using-the-wcf-development-tools)|討論如何建立和測試中的 WCF 服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|
||[如何：新增、更新或移除 WCF 資料服務參考](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|討論如何參考及使用[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。|
|[服務參考的疑難排解](../data-tools/troubleshooting-service-references.md)|呈現服務的參考，以及如何讓它們可以發生的一些常見錯誤。|
|[偵錯 WCF 服務](../debugger/debugging-wcf-services.md)|描述常見的偵錯問題和偵錯 WCF 服務時，可能會遇到的技術。|
|[逐步解說：建立多層式架構 (N-Tier) 資料應用程式](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|提供用於建立具類型資料集以及將 TableAdapter 和資料集程式碼分成多個專案的逐步指示。|
|[設定服務參考對話方塊](../data-tools/configure-service-reference-dialog-box.md)|描述使用者介面項目**設定服務參考** 對話方塊。|

## <a name="reference"></a>參考資料

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>另請參閱

- [適用於 .NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)