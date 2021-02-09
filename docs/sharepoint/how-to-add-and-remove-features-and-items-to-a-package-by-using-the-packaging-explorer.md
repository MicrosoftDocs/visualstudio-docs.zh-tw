---
title: 封裝 Explorer：新增 & 移除功能 & 專案至封裝
titleSuffix: ''
description: 使用 Visual Studio 中的 [封裝瀏覽器]，來新增和移除 SharePoint 封裝的功能和專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eec1468fc2e0c51d7dea7aa5f3ffa808b484ec87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923571"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>如何：使用封裝瀏覽器加入和移除封裝的功能和專案
  若要設定套件以部署 SharePoint 專案和功能，您可以使用封裝瀏覽器。 您可以調整 .wsp 檔案內的 SharePoint 專案專案和功能。

 或者，您也可以使用封裝設計工具來查看和重新排序功能，以變更啟用順序。 如需詳細資訊，請參閱 [如何：使用封裝設計工具加入和移除封裝的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。

## <a name="open-the-packaging-explorer"></a>開啟封裝瀏覽器
 如果您的 Visual Studio 方案至少有一個 SharePoint 專案，您可以使用下列程式開啟封裝瀏覽器。 或者，當您查看功能或封裝設計工具時，封裝瀏覽器會自動開啟。 關閉所有功能和封裝設計工具之後，封裝瀏覽器也會關閉。

#### <a name="to-open-the-packaging-explorer"></a>開啟封裝瀏覽器

1. 在功能表列上，選擇 [ **View**  >  **Other Windows**  >  **封裝瀏覽器**]。

     **封裝瀏覽器** 會出現在 [**工具箱**] 中。

## <a name="adding-a-feature-to-a-package"></a>將功能加入封裝中
 您可以使用封裝瀏覽器，將新的和現有的功能加入封裝中。

#### <a name="to-add-a-sharepoint-feature"></a>若要加入 SharePoint 功能

1. 開啟 **封裝 Explorer**，開啟專案的快捷方式功能表，然後選擇 [ **加入功能**]。

#### <a name="to-move-an-existing-sharepoint-feature"></a>移動現有的 SharePoint 功能

1. 開啟 [ **封裝瀏覽器**]，然後執行下列其中一個步驟：

    - 將 **功能** 從一個專案拖曳至另一個專案。

    - 開啟功能的快捷方式功能表，選擇 [ **剪** 下]，開啟要移動功能的專案快捷方式功能表，然後選擇 [ **貼** 上]。

    > [!NOTE]
    > 如果您的方案中有一個以上的 SharePoint 專案，請使用此程序。

## <a name="validate-a-feature-or-package"></a>驗證功能或封裝
 您可以藉由驗證檔案來識別 SharePoint 功能和封裝中的潛在問題。 警告和錯誤會顯示在 [輸出] 視窗和 [錯誤清單] 視窗中。

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>驗證 SharePoint 功能或封裝

1. 開啟 [ **封裝瀏覽器**]。

2. 開啟功能或封裝的快捷方式功能表，然後選擇 [ **驗證**]。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
