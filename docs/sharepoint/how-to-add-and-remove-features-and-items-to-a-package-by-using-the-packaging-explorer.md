---
title: 封裝 Explorer：將 & 移除功能 & 專案新增至封裝
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3ea7e30737855cbbb9434e8763f4903d80b82da
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014550"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>如何：使用封裝瀏覽器新增和移除封裝中的功能和專案
  若要設定封裝以部署 SharePoint 專案和功能，您可以使用封裝瀏覽器。 您可以調整 .wsp 檔案內的 SharePoint 專案專案和功能。

 或者，您可以使用封裝設計工具來查看和重新排序功能，以變更啟用順序。 如需詳細資訊，請參閱[如何：使用封裝設計工具加入和移除封裝中的功能和專案](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)。

## <a name="open-the-packaging-explorer"></a>開啟封裝瀏覽器
 如果您的 Visual Studio 方案至少有一個 SharePoint 專案，您可以使用下列程式開啟封裝瀏覽器。 或者，當您查看功能或封裝設計工具時，會自動開啟 [封裝] Explorer。 關閉所有功能和封裝設計工具之後，封裝瀏覽器也會關閉。

#### <a name="to-open-the-packaging-explorer"></a>若要開啟封裝瀏覽器

1. 在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **封裝 Explorer**]。

     [**封裝瀏覽器**] 會出現在 [**工具箱**] 中。

## <a name="adding-a-feature-to-a-package"></a>將功能新增至封裝
 您可以使用 [封裝瀏覽器]，將新的和現有的功能加入封裝中。

#### <a name="to-add-a-sharepoint-feature"></a>若要加入 SharePoint 功能

1. 開啟 [**封裝瀏覽器**]，開啟專案的快捷方式功能表，然後選擇 [**加入功能**]。

#### <a name="to-move-an-existing-sharepoint-feature"></a>若要移動現有的 SharePoint 功能

1. 開啟 [**封裝瀏覽器**]，然後執行下列其中一個步驟：

    - 將某**項功能**從一個專案拖曳至另一個專案。

    - 開啟功能的快捷方式功能表，選擇 [**剪**下]，開啟要移動功能的專案快捷方式功能表，然後選擇 [**貼**上]。

    > [!NOTE]
    > 如果您的方案中有一個以上的 SharePoint 專案，請使用此程序。

## <a name="validate-a-feature-or-package"></a>驗證功能或封裝
 您可以藉由驗證檔案來識別 SharePoint 功能和套件中的潛在問題。 警告和錯誤會顯示在 [輸出] 視窗和錯誤清單] 視窗中。

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>若要驗證 SharePoint 功能或封裝

1. 開啟**封裝瀏覽器**。

2. 開啟功能或封裝的快捷方式功能表，然後選擇 [**驗證**]。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
