---
title: HOW TO：新增與移除對應的資料夾 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21ecf370134558d7b47faad1c215fa9a65019316
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646209"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>如何： 新增與移除對應的資料夾
  一些常用於在 SharePoint 中的資料夾，例如影像和配置、 深度內嵌中的檔案階層。 您可以將這些資料夾對應至 SharePoint 專案，可以更輕鬆地存取它們。 對應的資料夾是 SharePoint 專案中對應的實體位置中的 SharePoint Server 安裝檔案的資料夾。

 當您部署 SharePoint 應用程式時，對應的資料夾和所有子資料夾複製到伺服器方案套件 (.wsp) 的內容執行 SharePoint 的 SharePoint 資料夾樹狀結構中指定的位置。 這個位置由**部署位置**針對對應的資料夾所設定的屬性。 在 [對應] 資料夾中的任何子資料夾的相對**部署位置**的對應資料夾。 請注意，**部署位置**屬性，不是對應的資料夾，名稱會決定項目部署的位置。
您可以透過命令功能表列上的捷徑功能表，專案，將對應的資料夾新增至專案中。 您可以使用**加入 SharePoint 「 映像 」 的 [對應] 資料夾**並**加入 SharePoint"版面配置 」 資料夾**命令來新增這些對應最常用的資料夾。 您可以將任何其他可用的 SharePoint 資料夾對應至您的專案，使用**加入 SharePoint 對應資料夾**命令的捷徑功能表，然後指定 [在資料夾**加入 SharePoint 對應資料夾** ] 對話方塊。

## <a name="add-mapped-folders-to-a-project"></a>將對應的資料夾新增至專案
 下列程序描述如何將兩個對應的資料夾新增至視覺 web 組件專案。 若要開始，您可以建立視覺 web 組件專案。

#### <a name="to-add-mapped-folders-to-a-project"></a>若要將對應的資料夾新增至專案

1.  在功能表列上，選擇 [檔案] > [新增] > [專案]。

2.  在 **新的專案**對話方塊方塊中，展開  **Visual Basic**或**Visual C#**   節點，展開**Office/SharePoint**節點，然後選擇**SharePoint 方案**節點。

3.  在專案範本清單中，選擇**SharePoint 2013 視覺 Web 組件**範本。

4.  在 [**名稱**方塊中，輸入**TestProject1**，然後選擇 **[確定]** ] 按鈕。

5.  在  **SharePoint 自訂精靈**，選擇**完成**按鈕，以保留預設設定。

6.  在 **方案總管**，選擇專案節點，然後在功能表列上選擇 **專案** > **加入 SharePoint 「 映像 」 的 對應 資料夾**。

     名為的資料夾**映像**會出現在您的專案，並包含名為 TestProject1 的子資料夾。 此對應的資料夾會包含視覺 web 組件專案的映像。

7.  在 **方案總管**，選擇專案節點，然後在功能表列上選擇 **專案** > **加入 SharePoint 對應資料夾**以顯示**加入 SharePoint 對應資料夾** 對話方塊。

8.  在適用於對應的資料夾樹狀結構檢視中，選擇**資源**資料夾，然後選擇 **[確定]** 按鈕。

     名為的資料夾**資源**會出現在您的專案。 此資料夾可以儲存字串資源檔等項目。 子資料夾可以是適用於組織的內容對應的資料夾，但不是會自動建立當您使用新增的對應的資料夾**加入 SharePoint 對應資料夾**命令。 若要加入子資料夾，請選擇**資源**資料夾，然後在功能表列上選擇 **專案** > **新資料夾**。

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>變更對應的資料夾的部署位置
 根據預設，對應的資料夾新增至特定位置，相對於 SharePoint 的根安裝路徑，其語彙基元\<SharePointRoot > 表示。 不過，您可以變更這個位置，藉由變更**部署位置**的對應資料夾的屬性。 每個對應的資料夾都有它自己**部署位置**屬性。

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>若要變更的對應資料夾的部署位置

1.  在您稍早建立的專案，選擇對應的資料夾。

2.  在 [**屬性**] 視窗中，選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕**部署位置**屬性。

3.  在 [**加入 SharePoint 對應資料夾**] 對話方塊中，瀏覽至您想要對應的資料夾，指向的資料夾。

4.  選擇  節點，然後選擇**確定** 按鈕。

## <a name="rename-or-remove-mapped-folders"></a>重新命名或移除對應的資料夾

#### <a name="to-rename-or-remove-a-mapped-folder"></a>若要重新命名或移除對應的資料夾

1.  在您稍早建立的專案，選擇對應的資料夾。

2.  若要重新命名對應的資料夾，開啟其捷徑功能表，選擇**重新命名**，輸入新名稱，然後選擇 Enter 鍵。

     或者，您可以選擇您想要重新命名，請開啟對應的資料夾**屬性** 視窗中，然後將設定的值**資料夾名稱**屬性設為新的名稱。

3.  若要從專案移除對應的資料夾，開啟其捷徑功能表，選擇**刪除**，然後選擇**確定**按鈕在對話方塊中，以確認移除。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
