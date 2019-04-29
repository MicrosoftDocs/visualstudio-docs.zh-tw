---
title: 建立 SharePoint 的網站資料行、 內容類型和清單 |Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8cecb3e78cea90b927dc6b67b5b4a2cb50bfa87c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62581092"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>建立 SharePoint 網站資料行、 內容類型和清單
  Visual Studio 提供許多不同基本 SharePoint 項目，包括專案項目範本*列出*並*內容類型*，這兩者都可以合併網站資料行 (或*欄位*)。 內容類型和清單的新設計工具讓您就以往更容易建立這些項目。

## <a name="site-columns"></a>網站資料行
 網站資料行是可以加入至 SharePoint 專案的其中一種最基本的項目。 網站資料行代表資料類型，例如電話號碼、註解，或是連絡人清單中連絡人居住的城市。

 新的網站資料行專案項目範本可讓您比在舊版 Visual Studio 中更容易建立網站資料行。 建立新的網站資料行之後, 您可以修改網站資料行中的 XML *Elements.xml*檔案，以包含您想要的資訊，例如它的顯示名稱、 其資料類型和您想要設定才會出現在網站資料行群組SharePoint。 如需有關站台的資料行的詳細資訊，請參閱[資料行簡介](http://go.microsoft.com/fwlink/?LinkId=224996)。

## <a name="content-types-and-lists"></a>內容類型和清單
 內容類型和清單是 SharePoint 中最常使用的項目。

 內容類型負責定義 SharePoint 清單或文件庫中項目分類的中繼資料、工作流程和行為。 例如，您可以為連絡人清單或工作清單中的資訊建立內容類型。 連絡人內容類型可能包含像是名稱、電子郵件、電話號碼和位址等資料行。 您在網站層級定義的內容類型與網站中的任何清單或文件庫並不相關。 您可以對 SharePoint 網站上不同的清單或文件庫使用相同的內容類型。 您也可以在相同的清單或文件庫上使用數種內容類型。

 清單是指 SharePoint 中您可與其他人共用的資訊集合。 清單是由包含資料的數列資料行所組成。 清單的範例包括：工作清單、連絡人清單以及公告清單。

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中新的內容類型和清單設計工具，讓建立網站內容類型和清單的工作比在舊版 Visual Studio 中更簡單而直覺。 UI 可讓您以視覺化且熟悉的方式建構內容類型和清單，並且讓您排序和分組清單中的資料，以及使用群組標頭。 如需內容類型的詳細資訊，請參閱[內容類型](http://go.microsoft.com/fwlink/?LinkId=224997)。 如需清單的詳細資訊，請參閱[的清單表單](http://go.microsoft.com/fwlink/?LinkId=224998)並[清單檢視](http://go.microsoft.com/fwlink/?LinkId=224999)。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[逐步解說：建立 SharePoint 網站資料行、 內容類型和清單](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|示範如何建立用於自訂內容類型的網站資料行。 這個內容類型之後可在自訂清單中使用。|

## <a name="see-also"></a>另請參閱
- [在 SharePoint 2010 開發快速入門](http://go.microsoft.com/fwlink/?LinkId=225000)
