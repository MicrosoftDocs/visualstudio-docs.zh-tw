---
title: 建立 SharePoint 的網站資料行、內容類型和清單 |Microsoft Docs
titleSuffix: ''
description: 建立 SharePoint 的網站資料行、內容類型和清單。 Visual Studio 為這些類型的 SharePoint 專案提供專案專案範本。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dfdf94f58c0fa7ba40d7c08309f8ea57949310df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949021"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>建立 SharePoint 的網站資料行、內容類型和清單
  Visual Studio 為許多不同的基本 SharePoint 專案（包括 *清單* 和 *內容類型*）提供專案專案範本，這兩個專案都可以) 的 (或 *欄位* 中納入網站資料行。 內容類型和清單的新設計工具讓您就以往更容易建立這些項目。

## <a name="site-columns"></a>網站資料行
 網站資料行是可以加入至 SharePoint 專案的其中一種最基本的項目。 網站資料行代表資料類型，例如電話號碼、註解，或是連絡人清單中連絡人居住的城市。

 新的網站資料行專案項目範本可讓您比在舊版 Visual Studio 中更容易建立網站資料行。 建立新的網站資料行之後，您可以修改網站資料行的 *Elements.xml* 檔案中的 XML，以包含您想要的資訊，例如其顯示名稱、資料類型，以及您希望網站資料行出現在 SharePoint 中的群組。 如需網站資料行的詳細資訊，請參閱資料 [行簡介](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14))。

## <a name="content-types-and-lists"></a>內容類型和清單
 內容類型和清單是 SharePoint 中最常使用的項目。

 內容類型負責定義 SharePoint 清單或文件庫中項目分類的中繼資料、工作流程和行為。 例如，您可以為連絡人清單或工作清單中的資訊建立內容類型。 連絡人內容類型可能包含像是名稱、電子郵件、電話號碼和位址等資料行。 您在網站層級定義的內容類型與網站中的任何清單或文件庫並不相關。 您可以對 SharePoint 網站上不同的清單或文件庫使用相同的內容類型。 您也可以在相同的清單或文件庫上使用數種內容類型。

 清單是指 SharePoint 中您可與其他人共用的資訊集合。 清單是由包含資料的數列資料行所組成。 清單的範例包括：工作清單、連絡人清單以及公告清單。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中新的內容類型和清單設計工具，讓建立網站內容類型和清單的工作比在舊版 Visual Studio 中更簡單而直覺。 UI 可讓您以視覺化且熟悉的方式建構內容類型和清單，並且讓您排序和分組清單中的資料，以及使用群組標頭。 如需內容類型的詳細資訊，請參閱 [內容類型](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))。 如需清單的詳細資訊，請參閱 [列出表單](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) 和 [清單視圖](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14))。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[逐步解說：建立 SharePoint 的網站資料行、內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|示範如何建立用於自訂內容類型的網站資料行。 這個內容類型之後可在自訂清單中使用。|

## <a name="see-also"></a>另請參閱
- [在 SharePoint 2010 上開發開始](/sharepoint/dev/)
