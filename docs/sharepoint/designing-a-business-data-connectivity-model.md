---
title: 設計商務資料連線模型 |Microsoft Docs
description: " (BDC) 模型設計商務資料連線。 新增實體和方法。 定義方法參數。 加入篩選描述項。 驗證 BDC 模型。"
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fb1aa194688533855b7c5bd1d58a4e3b97ac749
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948838"
---
# <a name="design-a-business-data-connectivity-model"></a>設計商務資料連線模型
  您可以藉由將實體和方法加入至模型檔案，來開發商務資料連線 (BDC) 服務的模型。 實體描述資料欄位的集合。 例如，實體可以代表資料庫中的資料表。 方法會執行工作，例如新增、刪除或更新實體所表示的資料。 如需詳細資訊，請參閱將 [商務資料整合到 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)。

## <a name="add-entities"></a>新增實體
 您可以將 **實體** 從 Visual Studio 工具箱拖曳或複製到 BDC 設計 **工具** 上，藉以新增實體。 如需詳細資訊，請參閱 [如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)。

 在類別中定義實體的欄位。 例如，您可以將名為的欄位加入 `Address` 至 `Customer` 類別。 您可以將新類別加入至專案，或使用其他工具（例如物件關聯式設計工具 (O/R 設計工具) ）所建立的現有類別。 機構名稱和代表實體的類別名稱不一定要相符。 當您在模型中定義方法時，您可以將類別與實體建立關聯。

## <a name="add-methods"></a>新增方法
 當使用者在以您的模型為基礎的清單或網頁元件中查看、加入、更新或刪除資訊時，BDC 服務會在您的模型中呼叫方法。 您必須針對使用者可執行檔每個工作，將方法新增至模型。 從 [ **BDC 方法詳細資料** ] 視窗中選取五個基本方法類型的任一種，以建立方法。 下表說明 BDC 模型的五個基本方法。

|方法|描述|
|------------|-----------------|
|儀|傳回實體實例的集合。 當使用者開啟清單或網頁元件時呼叫。 如需詳細資訊，請參閱 [如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)。|
|特定搜尋|傳回特定的實體實例。 當使用者在清單中查看特定專案的詳細資料時呼叫。 如需詳細資訊，請參閱 [如何：加入特定的搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)。|
|建立者|將新的資料加入至實體的資料來源。 當使用者在以模型為基礎之清單的功能區上選擇 [ **新增專案** ] 按鈕時呼叫。 如需詳細資訊，請參閱 [如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)。|
|更新者|修改清單中的資料。 當使用者更新清單中的資訊時呼叫。 如需詳細資訊，請參閱 [如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)。|
|刪除者|移除資料。 當使用者從清單中刪除專案時呼叫。 如需詳細資訊，請參閱 [如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)。|

## <a name="define-method-parameters"></a>定義方法參數
 當您建立方法時，Visual Studio 加入適用于方法類型的輸入和輸出參數。 這些參數只是預留位置。 在大多數情況下，您必須修改參數，讓它們傳入或傳回正確的資料類型。 例如，根據預設，Finder 方法會傳回字串。 在大部分情況下，您會想要修改 Finder 方法的 return 參數，使其傳回實體的集合。 您可以藉由修改參數的類型描述元來完成這項工作。 型別描述項是描述參數資料型別的屬性（attribute）集合。 如需詳細資訊，請參閱 [如何：定義參數的類型描述](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)元。

 Visual Studio 可讓您在模型中的參數之間複製類型描述元。 例如，您可以 `CustomerTD` 針對方法的 return 參數定義名為的型別描述項 `GetCustomer` 。 您可以 `CustomerTD` 在 **BDC Explorer** 中複製類型描述元，然後將該類型描述元貼到方法的輸入參數中 `CreateCustomer` 。 這可防止您必須多次定義相同的類型描述項。

## <a name="method-instances"></a>方法實例
 當您建立方法時，Visual Studio 加入預設方法實例。 方法實例是方法的參考，加上參數的預設值。 單一方法可以有多個方法實例。 每個實例都是方法簽章和一組預設值的組合。 如需詳細資訊，請參閱 [如何：定義參數的類型描述](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)元。

 當您執行專案時，方法實例會出現在 SharePoint 清單上方的下拉式清單中。 使用者可以選擇方法實例來查看資料。

 若要將預設值加入至方法實例，您必須直接修改模型的 XML。 如需詳細資訊，請參閱 [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14))。

## <a name="add-filter-descriptors"></a>加入篩選描述項
 模型的取用者可能會想要取出符合某些準則之實體的實例。 若要啟用這項功能，您可以將篩選描述元加入至方法。 篩選描述項可讓模型取用者在執行之前將值傳遞給方法，以篩選方法結果集。 如需詳細資訊，請參閱 [如何：將篩選參數新增至作業，以限制外部系統的實例](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14))。

 SharePoint 提供數個功能，可讓使用者提供篩選值。 例如，商務資料 Web 組件提供篩選準則文字方塊。 使用者可以在文字方塊中輸入值，以限制清單中的資料。 如需如何將篩選描述元加入至方法的詳細資訊，請參閱 [如何：將篩選描述元加入至 Finder 方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。

### <a name="filter-descriptor-properties"></a>篩選描述項屬性
 您必須設定篩選描述項的 **相關聯類型描述** 元、 **名稱** 和 **類型** 屬性值。 所有其他屬性都是選擇性的。

 **相關聯的類型描述** 元屬性會將篩選描述元與輸入參數產生關聯。 當使用者提供篩選值時，BDC 服務會使用輸入參數將該值傳遞給方法。

 **Type** 屬性描述您想要使用的篩選模式。 在 SharePoint 中，您選取的篩選模式會影響出現在消費者介面 (UI) 中的文字。 例如，在比較子篩選模式中，文字 **等於** 顯示為商務資料網頁元件上方的控制項。 如需每個篩選模式的詳細資訊，請參閱 [BDC 所支援的篩選類型](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))。

 如需篩選描述元屬性的詳細資訊，請參閱 [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14))。

### <a name="provide-default-values"></a>提供預設值
 在某些情況下，使用者可能不會提供篩選值。 您可以藉由將預設值加入方法實例，或在方法的程式碼中設定預設值，來提供預設值。 如需如何將預設值加入方法實例的詳細資訊，請參閱 [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))。 如需如何在方法的程式碼中設定輸入參數之預設值的範例，請參閱 [如何：將篩選描述元新增至搜尋工具方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)。

## <a name="validate-the-model"></a>驗證模型
 您可以在開發期間驗證您的模型。 Visual Studio 識別可能會讓您的模型無法如預期般運作的問題。 這些問題都會出現在 Visual Studio **錯誤清單** 中。

 您可以開啟 BDC 設計工具的快捷方式功能表，然後選擇 [ **驗證**]，以驗證模型。 如果模型包含任何錯誤，則會出現在 [ **錯誤清單**] 中。 按兩下清單中的錯誤，即可快速將游標移至包含錯誤的程式碼。 或者，您可以重複選擇 **F8** 或 **Shift** + **f8** 鍵，在清單中向前或向後跳到錯誤。

 以某種方式違反模型的規則時，就會發生驗證錯誤。 例如，如果類型描述項的 **IsCollection** 屬性設定為 **true**，但沒有任何子類型描述元，則會出現驗證錯誤。 您可能必須參考 BDC 模型的規則，才能瞭解 Visual Studio **錯誤清單** 中出現的一些錯誤。 如需有關 BDC 模型規則的詳細資訊，請參閱 [BDCMetadata 架構](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14))。

## <a name="debug-the-solution-that-contains-the-model"></a>將包含模型的方案進行 Debug 錯
 您可以對程式碼進行偵錯工具，就像在 Visual Studio 中進行程式碼的偵錯工具一樣。 若要對程式碼進行偵錯工具，請在程式碼中的任何位置設定中斷點，然後啟動偵錯工具。 Visual Studio 會開啟 SharePoint 網站。 在 SharePoint 中，建立使用您商務資料的清單或網頁元件。 然後，您可以逐步執行程式碼。 如需有關偵錯工具 SharePoint 專案的詳細資訊，請參閱 [疑難排解 sharepoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。

 您也可以在新增至專案的自訂群組件中，進行程式碼的偵錯工具。 不過，若要在自訂群組件中進行程式碼的偵錯工具，您必須將元件加入至方案套件。 如需詳細資訊，請參閱 [如何：加入和移除其他元件](../sharepoint/how-to-add-and-remove-additional-assemblies.md)。

 如需將自訂群組件加入至專案的詳細資訊，請參閱 [如何：在 BDC 功能中包含自訂群組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)。

### <a name="configure-bdc-security"></a>設定 BDC 安全性
 您可能必須先修改 SharePoint 中的安全性設定，才能將方案進行偵錯工具。 若要修改這些設定，請在 SharePoint 2010 管理中心網站中開啟商務資料連線服務應用程式。 在 [ **設定中繼資料存放區許可權** ] 對話方塊中，加入您的使用者帳戶，然後選取下列任何一個選項：

|Task|選項|
|----------|------------|
|將模型部署至 BDC 服務。|編輯|
|若要使用外部內容類型來建立清單和 Web 組件，請 (模型中) 實體。|在用戶端中可選取|
|建立、讀取、更新和刪除實體資料。|執行|

 如需這些設定的詳細資訊，請參閱 [商務資料連線服務管理](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14))。

 您也可以設定個別模型或外部內容類型的安全性許可權。 如需有關如何設定模型安全性許可權的詳細資訊，請參閱 [BDC 模型管理](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14))。 如需有關如何設定外部內容類型安全性許可權的詳細資訊，請參閱 [外部內容類型管理](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14))。

> [!NOTE]
> 您可以使用這些設定，在本機 SharePoint 伺服器上進行解決方案的偵錯工具。 如需有關如何在生產 SharePoint 伺服器上設定 BDC 相關安全性設定的詳細資訊，請參閱 [商務資料連線服務安全性總覽](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14))。

### <a name="retract-models-that-become-corrupt"></a>已損毀的撤回模型
 當您第一次啟動偵錯工具時，Visual Studio 會將整個模型部署到 SharePoint。 Visual Studio 之後，會使用您在部署之間進行的任何變更來更新 SharePoint 中的模型。

 在某些情況下，您可能會想要 Visual Studio 完全從 SharePoint 撤銷模型。 例如，模型可能會損毀。  若要將模型重新部署至 SharePoint，請將模型的 [累加 **式更新** ] 屬性設定為 [ **False**]，然後啟動偵錯工具。 當您在 **BDC Explorer** 中選取代表模型的節點時，[累加 **式更新**] 屬性會出現在 [**屬性**] 視窗中。 根據預設，模型的名稱是 **BdcModel1**。

### <a name="change-identifier-names-of-entities-in-the-model"></a>變更模型中實體的識別碼名稱
 如果您在部署模型之後變更識別碼的名稱，可能會收到部署錯誤。 您無法藉由將模型的 [累加 **式更新** ] 屬性設定為 [ **False**] 來解決這個錯誤。 您必須手動撤銷模型，然後重新部署方案。 如需詳細資訊，請參閱 [疑難排解 SharePoint 方案](../sharepoint/troubleshooting-sharepoint-solutions.md)。 您可以在最初部署模型之前，將累加 **式更新** 屬性設為 **False** ，以避免此錯誤。

## <a name="locate-documentation-for-bdc-model-elements"></a>尋找 BDC 模型元素的檔
 Visual Studio 針對您所建立的每個實體、方法或其他專案，將 XML 專案加入至模型。 元素屬性會在 [ **屬性** ] 視窗中顯示為屬性。 如需當您設計模型時 Visual Studio 產生之元素和屬性的詳細資訊，請參閱 [BDCMetadata 架構](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14))。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[BDC 模型設計工具總覽](../sharepoint/bdc-model-design-tools-overview.md)|描述您可以用來以視覺化方式設計 BDC 模型的工具。|
|[如何：將實體加入至模型](../sharepoint/how-to-add-an-entity-to-a-model.md)|示範如何將外部內容類型或實體新增至模型。|
|[如何：加入搜尋工具方法](../sharepoint/how-to-add-a-finder-method.md)|示範如何新增可讓使用者在清單或網頁元件中查看實體清單的方法。|
|[如何：新增特定搜尋工具方法](../sharepoint/how-to-add-a-specific-finder-method.md)|說明如何新增可讓使用者查看特定實體詳細資料的方法。|
|[如何：新增建立者方法](../sharepoint/how-to-add-a-creator-method.md)|示範如何加入可讓使用者直接從清單或 Web 元件將記錄新增至資料來源的方法。|
|[如何：加入刪除者方法](../sharepoint/how-to-add-a-deleter-method.md)|示範如何使用清單或 Web 元件的消費者介面 (UI) 中的選項，加入可讓使用者從資料來源移除資料的方法。|
|[如何：加入更新程式方法](../sharepoint/how-to-add-an-updater-method.md)|說明如何加入可讓使用者直接從清單或 Web 元件變更資料來源中資料記錄的方法。|
|[如何：將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)|說明如何使用 Visual Studio 中的 [方法詳細資料] 視窗，將輸入和傳回參數加入至方法。|
|[如何：定義參數的類型描述元](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|說明如何定義模型中的參數資料類型。|
|[如何：定義方法實例](../sharepoint/how-to-define-a-method-instance.md)|說明如何建立 BDC 所執行之方法的實例。|
|[如何：將篩選描述元新增至搜尋工具方法](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|說明如何讓使用者限制搜尋工具方法所傳回的實例數目。|
|[建立實體之間的關聯](../sharepoint/creating-an-association-between-entities.md)|描述如何在模型中定義實體之間的關聯性。 商務資料 Web 組件、外部清單和自訂應用程式可以在使用者介面中顯示這些資料關聯性 (UI) 。|
|[如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)|說明如何在模型中定義實體之間的關聯性。|
|[逐步解說：使用商務資料在 SharePoint 中 Createan 外部清單](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|提供逐步指示，說明如何建立和測試可在 SharePoint 外部清單中顯示連絡人的模型。|
|[將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|概述如何建立及設計 BDC 服務的模型。|
