---
title: 設計商務資料連接模型 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf2fd868927a7e8380d5c079c2f8dc86d5385961
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628412"
---
# <a name="design-a-business-data-connectivity-model"></a>設計商務資料連接模型
  您可以藉由將模型檔案中的實體和方法來開發商務資料連接 (BDC) 服務的模型。 實體描述資料欄位的集合。 例如，實體可以代表資料庫中的資料表。 方法會執行的工作，例如加入、 刪除或更新實體將代表的資料。 如需詳細資訊，請參閱 <<c0> [ 將商務資料整合到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)。

## <a name="add-entities"></a>新增實體
 您可以將實體拖曳或複製**實體**從 Visual Studio**工具箱**在 BDC 設計工具上。 如需詳細資訊，請參閱[如何：將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。

 在類別中定義之實體的欄位。 例如，您可以在其中加入名為的欄位`Address`至`Customer`類別。 您可以將新類別加入專案，或使用現有的類別使用物件關聯式設計工具 （O/R 設計工具） 等其他工具所建立。 實體的名稱和類別表示實體的名稱不必符合。 您在模型中定義的方法類別相關的實體。

## <a name="add-methods"></a>加入方法
 BDC 服務模型中呼叫方法，當使用者檢視、 新增、 更新或刪除清單或您的模型為基礎的 Web 組件中的資訊。 您必須將方法加入的使用者可以執行每項工作的模型。 五種基本方法類型從任一選取建立方法**BDC 方法詳細資料**視窗。 下表描述 BDC 模型的五個基本的方法。

|方法|描述|
|------------|-----------------|
|搜尋工具|傳回實體執行個體的集合。 當使用者開啟清單或 Web 組件時呼叫。 如需詳細資訊，請參閱[如何：新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)。|
|特定搜尋|傳回特定實體的執行個體。 當使用者在清單中檢視特定項目的詳細資料時呼叫。 如需詳細資訊，請參閱[如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)。|
|建立者|將新資料加入至資料來源的實體。 當使用者選擇時，呼叫**新的項目**清單是以模型為基礎的功能區上的按鈕。 如需詳細資訊，請參閱[如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)。|
|更新者|修改清單中的資料。 當使用者更新清單中的資訊時呼叫。 如需詳細資訊，請參閱[如何：新增更新者方法](../sharepoint/how-to-add-an-updater-method.md)。|
|刪除者|移除資料。 當使用者從清單中刪除項目時呼叫。 如需詳細資訊，請參閱[如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)。|

## <a name="define-method-parameters"></a>定義方法的參數
 當您建立一種方法時，Visual Studio 會新增適用於方法類型的輸入和輸出參數。 這些參數會只是預留位置。 在大部分情況下，您必須修改參數，讓它們在傳遞或傳回正確的資料類型。 例如，根據預設，搜尋工具方法會傳回字串。 在大部分情況下，您會想要修改搜尋方法的傳回參數，使它傳回之實體的集合。 您可以藉由修改參數的型別描述項來達到此目的。 型別描述項是描述參數的資料類型的屬性集合。 如需詳細資訊，請參閱[如何：定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。

 Visual Studio 可讓您複製模型中的參數之間的型別描述項。 例如，您可能會定義名為的型別描述元`CustomerTD`的傳回參數`GetCustomer`方法。 您可以複製`CustomerTD`型別描述項中的**BDC 總管**，然後貼上的輸入參數的類型描述元`CreateCustomer`方法。 這會防止您不必一次以上定義相同的型別描述項。

## <a name="method-instances"></a>方法執行個體
 當您建立一種方法時，Visual Studio 會新增預設方法執行個體。 方法執行個體是方法，再加上參數的預設值的參考。 單一方法可以有多個方法的執行個體。 方法簽章的組合和一組預設值的每個執行個體。 如需詳細資訊，請參閱[如何：定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)。

 當您執行專案時，方法執行個體出現在 SharePoint 清單上方的下拉式清單。 使用者可以選擇以檢視資料的方法執行個體。

 若要加入方法執行個體的預設值，您不必直接修改模型的 XML。 如需詳細資訊，請參閱 < [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279)。

## <a name="add-filter-descriptors"></a>加入篩選描述元
 模型的取用者可能會想要擷取符合某些準則之實體的執行個體。 若要啟用這項功能，您可以將篩選描述元新增至方法。 篩選描述元，讓模型以篩選方法的結果集之前執行，將值傳遞至方法的取用者。 如需詳細資訊，請參閱[如何：將篩選參數新增至作業，以限制從外部系統的執行個體](http://go.microsoft.com/fwlink/?LinkID=169267)。

 SharePoint 提供數個功能，讓使用者能夠提供篩選值。 例如，商務資料 Web 組件會提供 [篩選] 文字方塊。 使用者可以在文字方塊中輸入值來限制清單中的資料。 如需如何將篩選描述元加入至方法的詳細資訊，請參閱[How to:將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。

### <a name="filter-descriptor-properties"></a>篩選描述元屬性
 您必須設定的值**相關聯的型別描述項**，**名稱**，並**型別**篩選描述元的屬性。 所有其他屬性是選擇性的。

 **相關聯的型別描述項**屬性相關之輸入參數的篩選描述元。 當使用者提供篩選值時，BDC 服務該會將值傳遞至方法所使用的輸入的參數。

 **型別**屬性會描述您想要使用的篩選模式。 在 SharePoint 中，您選取的篩選模式會影響出現在使用者介面 (UI) 中的文字。 比方說，如比較子篩選模式，請將文字**等於**會顯示為上方商務資料 Web 組件控制項。 如需有關每個篩選模式的詳細資訊，請參閱 <<c0> [ 類型的支援篩選器的 BDC](http://go.microsoft.com/fwlink/?LinkId=169287)。

 如需有關的篩選描述元屬性的詳細資訊，請參閱[FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280)。

### <a name="provide-default-values"></a>提供預設值
 在某些情況下，使用者可能不會提供篩選值。 加入方法執行個體的預設值或方法的程式碼中設定的預設值，您可以提供預設值。 如需如何將預設值新增至方法的執行個體的詳細資訊，請參閱[MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)。 如需如何設定您的方法的程式碼中的輸入參數的預設值的範例，請參閱[How to:將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。

## <a name="validate-the-model"></a>驗證模型
 您可以在開發期間驗證您的模型。 Visual Studio 識別問題會妨礙您的模型如預期般運作。 這些問題出現在 Visual Studio**錯誤清單**。

 您可以驗證模型 BDC 設計工具中開啟捷徑功能表，然後選擇**驗證**。 如果模型包含任何錯誤，它們會出現在**錯誤清單**。 您可以快速地移動游標，按兩下清單中的錯誤訊息包含錯誤的程式碼。 或者，您可以選擇**F8**或是**Shift**+**F8**不斷地往前或往後透過錯誤清單中的步驟的金鑰。

 模型的規則違反以某種方式時，可能會發生驗證錯誤。 例如，如果**IsCollection**的型別描述項的屬性設定為 **，則為 true**，但沒有子型別描述項存在，將會顯示驗證錯誤。 您可能必須參考以了解在 Visual Studio 會出現一些錯誤 BDC 模型的規則**錯誤清單**。 BDC 模型的規則的相關資訊，請參閱[BDCMetadata 結構描述](http://go.microsoft.com/fwlink/?LinkID=169275)。

## <a name="debug-the-solution-that-contains-the-model"></a>包含模型的方案進行偵錯
 當您將偵錯在 Visual Studio 中的任何程式碼，您可以偵錯您的程式碼。 若要偵錯程式碼，程式碼中的任何位置設定中斷點，然後啟動偵錯工具。 Visual Studio 會開啟 SharePoint 網站。 在 SharePoint 中，以建立清單或使用您的商務資料的 Web 組件。 然後，您可以逐步執行程式碼。 如需有關偵錯 SharePoint 專案的詳細資訊，請參閱 <<c0> [ 疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。

 您也可以偵錯自訂組件加入至專案中的程式碼。 不過，偵錯自訂組件中的程式碼，您必須將組件新增至方案套件。 如需詳細資訊，請參閱[如何：新增和移除其他組件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。

 如需有關如何將自訂組件新增至您專案的詳細資訊，請參閱[How to:在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)。

### <a name="configure-bdc-security"></a>設定 BDC 安全性
 您可能必須修改您在 SharePoint 中的安全性設定，您可以偵錯您的解決方案之前。 若要修改這些設定，請開啟商務資料連接的服務應用程式在 SharePoint 2010 管理中心網站。 在 [**設定的中繼資料存放區使用權限**] 對話方塊中，新增您的使用者帳戶，然後選取下列任何選項：

|工作|選項|
|----------|------------|
|將模型部署到 BDC 服務。|編輯|
|若要建立清單和使用的 Web 組件外部內容類型 （實體），在模型中。|在用戶端中，您可選取|
|若要建立、 讀取、 更新和刪除實體的資料。|執行|

 如需有關這些設定的詳細資訊，請參閱 < [Business Data Connectivity 服務管理](http://go.microsoft.com/fwlink/?LinkID=178883)。

 您也可以設定個別的模型或外部內容類型的安全性權限。 如需如何設定安全性權限，模型的詳細資訊，請參閱[BDC 模型管理](http://go.microsoft.com/fwlink/?LinkID=178884)。 如需如何設定安全性權限的外部內容類型的詳細資訊，請參閱[外部內容類型管理](http://go.microsoft.com/fwlink/?LinkID=178885)。

> [!NOTE]
>  您可以使用這些設定，偵錯本機 SharePoint 伺服器上的解決方案。 如需如何在生產環境 SharePoint 伺服器上的 BDC 相關的安全性設定的詳細資訊，請參閱[Business Data Connectivity 服務安全性概觀](http://go.microsoft.com/fwlink/?LinkID=178886)。

### <a name="retract-models-that-become-corrupt"></a>撤銷損毀的模型
 第一次您啟動偵錯工具，Visual Studio，將整個模型部署到 SharePoint。 之後每次 Visual Studio 會更新 SharePoint 中的模型，與您所做的部署之間的任何變更。

 可能有您想要完全收回的模型，從 SharePoint 的 Visual Studio。 例如，模型可能會損毀。  若要重新部署您的模型，sharepoint，請設定**累加式更新**屬性的模型來**False**，然後啟動偵錯工具。 **累加式更新**屬性會出現在**屬性**視窗中，當您選取的模型中表示的節點時**BDC 總管**。 根據預設，模型的名稱是**BdcModel1**。

### <a name="change-identifier-names-of-entities-in-the-model"></a>變更模型中實體的識別項名稱
 如果您在部署模型之後，您就會變更識別項的名稱，您可能會收到部署錯誤。 您無法解決此錯誤，藉由設定**累加式更新**屬性的模型來**False**。 您必須手動撤銷模型，並再重新部署解決方案。 如需詳細資訊，請參閱 <<c0> [ 疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。 您可以避免這個錯誤，藉由設定**累加式更新**屬性設**False**最初部署模型之前。

## <a name="locate-documentation-for-bdc-model-elements"></a>通道接收的文件，BDC 模型項目
 Visual Studio 在每個實體，模型中加入 XML 項目方法或其他您所建立的項目。 元素屬性會顯示為中的屬性**屬性**視窗。 如需 Visual Studio 會產生當您設計模型的屬性與項目資訊，請參閱[BDCMetadata 結構描述](http://go.microsoft.com/fwlink/?LinkID=169275)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)|描述您可用來以視覺化方式設計 BDC 模型的工具。|
|[如何：將實體新增至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)|說明如何將外部內容類型或實體加入至模型。|
|[如何：新增搜尋方法](../sharepoint/how-to-add-a-finder-method.md)|說明如何新增可讓使用者檢視的實體清單，清單或 Web 組件中的方法。|
|[如何：新增特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)|示範如何加入的方法，可讓使用者檢視在特定實體的詳細資料。|
|[如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)|示範如何加入的方法，可讓使用者直接從清單或 Web 組件時，將記錄新增至資料來源。|
|[如何：新增刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)|示範如何加入的方法，可讓使用者以移除資料來源中的資料，利用使用者介面 (UI) 的清單或 Web 組件中的選項。|
|[如何：新增更新者方法](../sharepoint/how-to-add-an-updater-method.md)|示範如何加入的方法，可讓使用者直接從清單或 Web 組件中變更資料來源中的資料記錄。|
|[如何：新增參數至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)|說明如何使用 Visual Studio 中的 [方法詳細資料] 視窗新增至方法的輸入和傳回參數。|
|[如何：定義參數的型別描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|說明如何在模型中定義的參數資料類型。|
|[如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)|說明如何建立 BDC 執行的方法的執行個體。|
|[如何：將篩選描述元加入至搜尋方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|說明如何讓使用者以限制傳回的搜尋方法的執行個體數目。|
|[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)|描述如何定義模型中實體之間的關聯性。 商務資料 Web 組件、 外部清單，與自訂應用程式可以顯示使用者介面 (UI) 中的這些資料關聯性。|
|[如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)|說明如何定義模型中實體之間的關聯性。|
|[逐步解說：建立外部清單在 SharePoint 中使用商務資料](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|提供逐步指示，說明如何建立和測試的模型，在 SharePoint 外部的清單中顯示的連絡人。|
|[將商務資料整合到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|提供建立和設計的 BDC 服務模型的概觀。|
