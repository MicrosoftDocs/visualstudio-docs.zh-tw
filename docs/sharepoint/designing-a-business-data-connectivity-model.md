---
title: "設計商務資料連接模型 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 886522cacff9359b3516b9e09530bfb1c41acfe6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="designing-a-business-data-connectivity-model"></a>設計商務資料連接模型
  您可以將實體和方法加入至模型檔案來開發商務資料連線 (BDC) 服務的型號。 實體會描述資料欄位的集合。 例如，實體可以代表資料庫中的資料表。 方法執行的工作，例如加入、 刪除或更新實體將代表的資料。 如需詳細資訊，請參閱[整合至 SharePoint 的商務資料](../sharepoint/integrating-business-data-into-sharepoint.md)。  
  
## <a name="adding-entities"></a>加入實體  
 您可以將實體拖曳或複製**實體**從 Visual Studio**工具箱**在 BDC 設計工具上。 如需詳細資訊，請參閱[How to： 將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。  
  
 類別中定義實體的欄位。 例如，您可能會加入名為的欄位`Address`至`Customer`類別。 您可以將新類別加入至專案，或使用現有的類別使用物件關聯式設計工具 （O/R 設計工具） 等其他工具所建立。 實體的名稱和類別代表實體的名稱不必符合。 您在模型中定義之方法的類別相關的實體。  
  
## <a name="adding-methods"></a>加入方法  
 當使用者檢視、 新增、 更新或刪除清單或 Web 組件，取決於您的模型中的資訊時，BDC 服務模型中呼叫方法。 您必須將方法加入至模型的使用者可以執行每項工作。 建立方法，藉由選取任何五種基本方法類型從**BDC 方法詳細資料**視窗。 下表描述 BDC 模型的五種基本方法。  
  
|方法|描述|  
|------------|-----------------|  
|搜尋|傳回實體執行個體的集合。 當使用者開啟的清單或 Web 組件時呼叫。 如需詳細資訊，請參閱[如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)。|  
|特定搜尋|傳回特定實體執行個體。 當使用者檢視清單中的特定項目的詳細資料時呼叫。 如需詳細資訊，請參閱[如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)。|  
|建立者|將新資料加入至資料來源的實體。 當使用者選擇時，呼叫**新項目**清單中的模型為基礎的功能區上的按鈕。 如需詳細資訊，請參閱[如何： 加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)。|  
|更新者|修改清單中的資料。 當使用者更新清單中的資訊時呼叫。 如需詳細資訊，請參閱[How to: Add Updater 方法](../sharepoint/how-to-add-an-updater-method.md)。|  
|刪除者|移除資料。 當使用者從清單中刪除項目時呼叫。 如需詳細資訊，請參閱[如何： 加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)。|  
  
## <a name="defining-method-parameters"></a>定義方法的參數  
 當您建立一種方法時，Visual Studio 會加入適當的方法類型的輸入和輸出參數。 這些參數是只是預留位置。 在大部分情況下，您必須修改的參數，讓它們在傳遞或傳回正確的資料類型。 例如，根據預設，搜尋工具方法傳回的字串。 在大部分情況下，您會想要修改搜尋方法的傳回參數，使它傳回實體的集合。 您可以完成，藉由修改參數的類型描述元。 類型描述元是描述參數的資料類型的屬性集合。 如需詳細資訊，請參閱[如何： 定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
 Visual Studio 可讓您複製模型中的參數之間的類型描述元。 例如，您可以定義名為的類型描述元`CustomerTD`的傳回參數`GetCustomer`方法。 您可以複製`CustomerTD`類型描述元中的**BDC 總管**，然後貼上的輸入參數的類型描述元`CreateCustomer`方法。 這可讓您不必一次以上定義的相同的類型描述元。  
  
##  <a name="MethodInstances"></a>方法執行個體  
 當您建立的方法時，Visual Studio 會加入預設方法執行個體。 方法執行個體是一種方法，再加上參數的預設值的參考。 單一方法可以有多個方法的執行個體。 每個執行個體是方法簽章的組合和一組預設值。 如需詳細資訊，請參閱[如何： 定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。  
  
 當您執行專案時，方法執行個體出現在 SharePoint 清單上方的下拉式清單。 使用者可以選擇以檢視資料的方法執行個體。  
  
 若要將預設值加入至方法的執行個體，您必須直接修改模型的 XML。 如需詳細資訊，請參閱[DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279)。  
  
## <a name="adding-filter-descriptors"></a>加入篩選描述元  
 模型的取用者可能想要擷取的實體符合某些準則的執行個體。 若要啟用這項功能，您可以將篩選描述元加入至方法。 篩選描述元啟用模型來篩選方法的結果集之前，它們執行，將值傳遞至方法的取用者。 如需詳細資訊，請參閱[How to： 將篩選參數加入至作業，以限制的執行個體從外部系統](http://go.microsoft.com/fwlink/?LinkID=169267)。  
  
 SharePoint 提供數個功能，讓使用者能夠提供篩選值。 例如，商務資料 Web 組件會提供篩選的文字方塊。 使用者可以在文字方塊中輸入值來限制清單中的資料。 如需如何將篩選描述元加入至方法的詳細資訊，請參閱[How to： 將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。  
  
### <a name="filter-descriptor-properties"></a>篩選描述元屬性  
 您必須設定的值**相關聯的類型描述元**，**名稱**，和**類型**篩選描述元屬性。 所有其他屬性是選擇性的。  
  
 **相關聯的類型描述元**屬性關聯的篩選描述元之輸入參數。 當使用者提供篩選值時，BDC 服務該會將值傳遞至方法使用輸入的參數。  
  
 **類型**屬性會描述您想要使用的篩選模式。 在 SharePoint 中，您選取的篩選模式會影響出現在使用者介面 (UI) 中的文字。 例如，對於比較子篩選模式，文字**等於**會顯示為上方商務資料 Web 組件的控制項。 如需每個篩選模式的詳細資訊，請參閱[類型的篩選條件受到 BDC](http://go.microsoft.com/fwlink/?LinkId=169287)。  
  
 如需篩選描述元的屬性的詳細資訊，請參閱[FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280)。  
  
### <a name="providing-default-values"></a>提供預設值  
 在某些情況下，使用者可能無法提供篩選值。 藉由加入方法執行個體的預設值或方法的程式碼中設定的預設值，您可以提供預設值。 如需如何新增方法執行個體的預設值的詳細資訊，請參閱[MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。 如需如何在您的方法的程式碼中設定的輸入參數的預設值的範例，請參閱[How to： 將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。  
  
## <a name="validating-the-model"></a>驗證模型  
 您可以在開發期間驗證您的模型。 Visual Studio 可以識別問題會造成您的模型無法如預期般運作。 這些問題會出現在 Visual Studio**錯誤清單**。  
  
 您可以驗證模型 BDC 設計工具中開啟捷徑功能表，然後選擇**驗證**。 如果模型包含任何錯誤，它們會出現在**錯誤清單**。 您可以快速移動游標，連按兩下清單中的錯誤訊息包含錯誤的程式碼。 或者，您可以選擇下 F8 或 Shift + F8 鍵不斷地向前走或向錯誤清單中。  
  
 以某種方式違反規則的模型時，可能會發生驗證錯誤。 例如，如果**IsCollection**屬性的類型描述元設定為**true**，但沒有子類型描述項存在，會出現驗證錯誤。 您必須了解 Visual Studio 中會出現一些錯誤 BDC 模型的規則是指**錯誤清單**。 BDC 模型的規則的相關資訊，請參閱[BDCMetadata 結構描述](http://go.microsoft.com/fwlink/?LinkID=169275)。  
  
## <a name="debugging-the-solution-that-contains-the-model"></a>偵錯包含模型的方案  
 當您將偵錯 Visual Studio 中的任何程式碼，您可以偵錯您的程式碼。 偵錯您的程式碼，請在程式碼中的任何位置設定中斷點，然後再啟動 偵錯工具。 Visual Studio 會開啟 SharePoint 網站。 在 SharePoint 中，以建立清單或使用您的商務資料 Web 組件。 然後，您可以逐步執行程式碼。 如需有關偵錯 SharePoint 專案的詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。  
  
 您也可以偵錯程式碼加入至專案的自訂組件中。 不過，偵錯自訂組件中的程式碼，您必須將組件加入至方案套件。 如需詳細資訊，請參閱[如何： 加入和移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。  
  
 如需將自訂組件加入您專案的詳細資訊，請參閱[How to： 在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)。  
  
### <a name="configuring-bdc-security"></a>設定 BDC 安全性  
 您可能必須修改您在 SharePoint 中的安全性設定，您可以在偵錯您的方案之前。 若要修改這些設定，開啟 商務資料連接服務應用程式在 SharePoint 2010 中央系統管理網站。 在**設定中繼資料存放區權限**對話方塊中，加入您的使用者帳戶，然後選取下列任何選項：  
  
|工作|選項|  
|----------|------------|  
|若要將模型部署到 BDC 服務。|Edit|  
|若要建立清單和使用 Web 組件外部內容類型 （實體），在模型中。|在用戶端中可選取|  
|若要建立、 讀取、 更新和刪除實體的資料。|執行|  
  
 如需有關這些設定的詳細資訊，請參閱[商務資料連接服務管理](http://go.microsoft.com/fwlink/?LinkID=178883)。  
  
 您也可以設定個別的模型或外部內容類型的安全性權限。 如需如何設定模型的安全性權限的詳細資訊，請參閱[BDC 模型管理](http://go.microsoft.com/fwlink/?LinkID=178884)。 如需如何設定外部內容類型的安全性權限的詳細資訊，請參閱[外部內容類型管理](http://go.microsoft.com/fwlink/?LinkID=178885)。  
  
> [!NOTE]  
>  若要偵錯您的本機 SharePoint 伺服器上之解決方案中使用這些設定。 如需如何在實際執行 SharePoint 伺服器上設定 BDC 與相關的安全性設定的詳細資訊，請參閱[Business Data Connectivity 服務安全性概觀](http://go.microsoft.com/fwlink/?LinkID=178886)。  
  
### <a name="retracting-models-that-become-corrupt"></a>撤銷損毀的模型  
 第一次您啟動偵錯工具，Visual Studio 會將整個模型部署至 SharePoint。 此後每次 Visual Studio 會使用您的部署之間進行任何變更更新 SharePoint 中的模型。  
  
 可能會有您想要讓 Visual Studio，若要完全撤回 SharePoint 中的模型。 例如，模型可能會損毀。  若要重新部署您的模型至 SharePoint，請設定**累加式更新**屬性要模型**False**，然後開始偵錯工具。 **累加式更新**屬性會出現在**屬性**選取代表的模型中的節點時，視窗**BDC 總管**。 根據預設，模型的名稱是**BdcModel1**。  
  
### <a name="changing-identifier-names-of-entities-in-the-model"></a>變更模型中實體的識別項名稱  
 如果您部署模型之後，您可以變更的識別項名稱，您可能會收到部署錯誤。 您無法解決此錯誤，藉由設定**累加式更新**屬性要模型**False**。 您必須手動撤銷模型，然後再重新部署方案。 如需詳細資訊，請參閱[疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。 您可以避免這個錯誤，藉由設定**累加式更新**屬性**False**您一開始會部署模型之前。  
  
## <a name="locating-documentation-for-bdc-model-elements"></a>尋找 BDC 模型項目的文件  
 Visual Studio 會將 XML 項目加入至每個實體，模型方法或您建立其他項目。 項目屬性中做為屬性出現**屬性**視窗。 如需項目和 Visual Studio 會產生如您設計模型的屬性資訊，請參閱[BDCMetadata 結構描述](http://go.microsoft.com/fwlink/?LinkID=169275)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)|描述可讓您以視覺化方式設計 BDC 模型的工具。|  
|[如何：將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)|示範如何將外部內容類型或實體加入至模型。|  
|[如何：新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)|示範如何加入的方法，可讓使用者檢視實體的清單，清單或 Web 組件中。|  
|[如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)|示範如何加入的方法，可讓使用者檢視在特定實體的詳細資料。|  
|[如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)|示範如何加入的方法，可讓使用者直接從清單或 Web 組件，將記錄加入至資料來源。|  
|[如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)|示範如何加入的方法，可讓使用者透過使用者介面 (UI) 的清單或 Web 組件中的選項移除資料來源的資料。|  
|[如何：新增更新者方法](../sharepoint/how-to-add-an-updater-method.md)|示範如何加入的方法，可讓使用者直接從清單或 Web 組件中變更資料來源中的資料記錄。|  
|[如何：將參數新增至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)|示範如何使用 Visual Studio 中的 [方法詳細資料] 視窗將輸入和傳回參數加入至方法。|  
|[如何：定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|示範如何在模型中定義參數資料類型。|  
|[如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)|示範如何建立 BDC 執行方法的執行個體。|  
|[如何：將篩選描述元新增至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|示範如何讓使用者進行的搜尋工具方法所傳回的執行個體的數目。|  
|[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)|描述如何定義模型中實體之間的關聯性。 商務資料 Web 組件、 外部清單，與自訂應用程式可以顯示使用者介面 (UI) 中的這些資料關聯性。|  
|[如何： 建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)|示範如何定義模型中實體之間的關聯性。|  
|[逐步解說：使用商務資料在 SharePoint 中建立外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|提供逐步指示，說明如何建立及測試模型的 SharePoint 外部清單中顯示的連絡人。|  
|[將商業資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|提供建立及設計 BDC 服務模型的概觀。|  
  
  