---
title: 建立實體之間的關聯 |Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee767ded0687baa09653bd82785b68bee7fa0ebd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981083"
---
# <a name="create-an-association-between-entities"></a>建立實體之間的關聯
  您可以藉由建立關聯，在商務資料連線（BDC）模型中定義實體之間的關係。 Visual Studio 會產生方法，以提供模型的取用者與每個關聯的相關資訊。 這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 (UI) 中顯示資料關聯性。

## <a name="create-an-association"></a>建立關聯
 選擇 [Visual Studio**工具箱**] 中的 [**關聯**] 控制項，選擇第一個實體（稱為 [來源] 實體），然後選擇第二個實體（稱為 [目的地] 實體），以建立關聯。 您可以在 [**關聯編輯器**] 中定義關聯的詳細資料。 如需詳細資訊，請參閱[如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)。

## <a name="association-methods"></a>關聯方法
 SharePoint 商務資料 web 元件之類的應用程式會藉由呼叫實體的服務類別中的方法來取用關聯。 您可以藉由在 [**關聯編輯器**] 中選取，將方法加入至實體的服務類別。

 根據預設，[**關聯編輯器**] 會將關聯流覽方法加入至來源和目的地實體。 來源實體中的關聯流覽方法，可讓取用者抓取目的地實體的清單。 目的地實體中的關聯流覽方法，可讓取用者抓取與目的地實體相關的來源實體。

 您必須將程式碼新增至每個方法，以傳回適當的資訊。 您也可以新增其他類型的方法，以支援更先進的案例。 如需有關這些方法的詳細資訊，請參閱[支援的作業](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))。

## <a name="types-of-associations"></a>關聯的類型
 您可以在 BDC 設計工具中建立兩種類型的關聯： [外鍵關聯] 和 [外部無索引鍵關聯]。

### <a name="foreign-key-based-association"></a>外鍵型關聯
 您可以建立外鍵型關聯，方法是將來源實體中的識別碼與目的地實體中定義的型別描述項相關聯。 此關聯性可讓模型的取用者為其使用者提供增強的 UI。 例如，Outlook 中的表單可讓使用者建立可在下拉式清單中顯示客戶的銷售訂單;或 SharePoint 中的銷售訂單清單，可讓使用者開啟客戶的設定檔頁面面。

 若要建立外鍵型關聯，請關聯共用相同名稱和類型的識別碼和類型描述元。 例如，您可以建立 `Contact` 實體與 `SalesOrder` 實體之間的外鍵關聯。 `SalesOrder` 實體會傳回 `ContactID` 型別描述元，做為 Finder 或特定搜尋工具方法的傳回參數之一部分。 這兩個型別描述元都會出現在 [**關聯編輯器**] 中。 若要建立 `Contact` 實體與 `SalesOrder` 實體之間的外鍵關聯性，請選擇每個欄位旁邊的 `ContactID` 識別碼。

 將程式碼加入至來源實體的關聯導覽器方法，以傳回目的地實體的集合。 下列範例會傳回連絡人的銷售訂單。

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 將程式碼新增至目的地實體的關聯導覽器方法，以傳回來源實體。 下列範例會傳回與銷售訂單相關的連絡人。

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>外部無索引鍵關聯
 您可以建立關聯，而不將識別碼對應至欄位類型描述元。 當來源實體沒有與目的地實體的直接關聯性時，請建立這種關聯。 例如，`SalesOrderDetail` 資料表沒有對應至 `Contact` 資料表中主鍵的外鍵。

 如果您想要在與 `Contact`相關的 `SalesOrderDetail` 資料表中顯示資訊，您可以在 [`Contact` 實體] 和 [`SalesOrderDetail`] 實體之間建立外部無索引鍵關聯。

 在 `Contact` 實體的關聯導覽方法中，藉由聯結資料表或呼叫預存程式來傳回 `SalesOrderDetail` 實體。

 下列範例會藉由聯結資料表來傳回所有銷售訂單的詳細資料。

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 在 `SalesOrderDetail` 實體的關聯導覽方法中，傳回相關的 `Contact`。 下列範例為其示範。

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>請參閱
- [設計商務資料連線模型](../sharepoint/designing-a-business-data-connectivity-model.md)
- [如何：建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)
