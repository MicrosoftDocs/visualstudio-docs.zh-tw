---
title: 建立實體之間的關聯 |Microsoft Docs
description: 建立商務資料連線中實體之間的關聯 (BDC) 模型。 瞭解關聯方法和關聯的類型。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d40c4e5c5d61b9da3cdbdd3fe96f45c4a0cff929
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213962"
---
# <a name="create-an-association-between-entities"></a>建立實體之間的關聯
  您可以藉由建立關聯來定義商務資料連線中實體之間的關聯性 (BDC) 模型。 Visual Studio 會產生可提供模型取用者的方法，以及每個關聯的相關資訊。 這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 (UI) 中顯示資料關聯性。

## <a name="create-an-association"></a>建立關聯
 選擇 [Visual Studio]**工具箱** 中的 [**關聯**] 控制項，選擇稱為 [來源]) 實體 (的第一個實體，然後選擇第二個實體 (稱為 [目的地實體]) ，即可建立關聯。 您可以在 **關聯編輯器** 中定義關聯的詳細資料。 如需詳細資訊，請參閱 [如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)。

## <a name="association-methods"></a>Association 方法
 SharePoint 商務資料網頁元件之類的應用程式會藉由呼叫實體服務類別中的方法來取用關聯。 您可以在 **關聯編輯器** 中選取方法，藉此將方法新增至實體的服務類別。

 根據預設，[ **關聯編輯器** ] 會將關聯導覽方法加入至來源和目的地實體。 來源實體中的關聯流覽方法可讓取用者取得目的實體清單。 目的地實體中的關聯流覽方法可讓取用者取得與目的地實體相關的來源實體。

 您必須將程式碼新增至上述每個方法，以傳回適當的資訊。 您也可以新增其他類型的方法來支援更先進的案例。 如需這些方法的詳細資訊，請參閱 [支援的作業](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))。

## <a name="types-of-associations"></a>關聯類型
 您可以在 BDC 設計工具中建立兩種類型的關聯：外鍵型關聯和外部無索引鍵關聯。

### <a name="foreign-key-based-association"></a>以外鍵為基礎的關聯
 您可以建立以外鍵為基礎的關聯，方法是將來源實體中的識別碼與目的地實體中定義的型別描述項產生關聯。 此關聯性可讓模型的取用者為其使用者提供增強的 UI。 例如 Outlook 中的表單，可讓使用者建立可在下拉式清單中顯示客戶的銷售訂單;或 SharePoint 中的銷售訂單清單，可讓使用者開啟客戶的設定檔頁面面。

 若要建立外鍵關聯，請建立共用相同名稱和類型的識別碼和類型描述元。 例如，您可以建立實體和實體之間的外鍵關聯 `Contact` `SalesOrder` 。 實體會傳回 `SalesOrder` `ContactID` 型別描述元，作為 Finder 或特定 finder 方法的 return 參數的一部分。 這兩個類型描述項都會出現在 **關聯編輯器** 中。 若要建立實體和實體之間的外鍵關聯性 `Contact` `SalesOrder` ，請選擇 `ContactID` 每個欄位旁的識別碼。

 將程式碼加入至來源實體的 [關聯導覽器] 方法，該方法會傳回目的地實體的集合。 下列範例會傳回連絡人的銷售訂單。

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet7":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet7":::

 將程式碼加入至傳回來源實體之目的地實體的關聯導覽器方法。 下列範例會傳回與銷售訂單相關的連絡人。

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet8":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet8":::

### <a name="foreign-keyless-association"></a>外部無索引鍵關聯
 您可以建立關聯，而不將識別碼對應至欄位類型描述元。 當來源實體與目的地實體沒有直接關聯性時，請建立這種關聯。 例如，資料表沒有 `SalesOrderDetail` 對應至資料表中主鍵的外鍵 `Contact` 。

 如果您想要在與 `SalesOrderDetail` 相關聯的資料表中顯示資訊 `Contact` ，您可以在 `Contact` 實體和實體之間建立外部無索引鍵關聯 `SalesOrderDetail` 。

 在實體的關聯流覽方法中 `Contact` ，藉 `SalesOrderDetail` 由聯結資料表或藉由呼叫預存程式來傳回實體。

 下列範例會藉由聯結資料表來傳回所有銷售訂單的詳細資料。

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet9":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet9":::

 在實體的關聯流覽方法中 `SalesOrderDetail` ，傳回相關的 `Contact` 。 下列範例示範此作業。
                                                                            
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet10":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet10":::

## <a name="see-also"></a>另請參閱
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)
