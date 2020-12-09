---
title: 如何：新增和移除對應的資料夾 |Microsoft Docs
description: 新增和移除 SharePoint 中專案的對應資料夾。  變更對應資料夾的部署位置。 重新命名或移除對應的資料夾。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: e4d29be9b008bfaa9ad6694725b03e25bf6847df
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914800"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>如何：新增和移除對應的資料夾
  SharePoint 中一些常用的資料夾（例如影像和版面配置）會在檔案階層中緊密內嵌。 您可以將這些資料夾對應到 SharePoint 專案，以便更輕鬆地存取這些資料夾。 對應的資料夾是 SharePoint 專案中對應至 SharePoint Server 安裝中檔案實體位置的資料夾。

 當您部署 SharePoint 應用程式時，方案)  ( 套件會將對應資料夾及其所有子資料夾的內容複寫到執行 SharePoint 的伺服器上，該伺服器會在 SharePoint 資料夾樹狀結構中的指定位置執行 SharePoint。 這個位置是由針對對應資料夾所設定的 [ **部署位置** ] 屬性所決定。 對應資料夾中的任何子資料夾都相對於對應資料夾的 **部署位置** 。 請注意，[ **部署位置** ] 屬性（而不是對應的資料夾名稱）會決定專案的部署位置。
您可以使用功能表列上的命令或專案的快捷方式功能表，將對應資料夾新增至專案。 您可以使用「 **新增 sharepoint」對應的資料夾** ，並 **新增 Sharepoint** 的「版面配置」資料夾命令，以新增最常使用的對應資料夾。 您可以使用快捷方式功能表上的 [ **加入 Sharepoint 對應資料夾** ] 命令，然後在 [ **加入 sharepoint 對應資料夾** ] 對話方塊中指定資料夾，將任何其他可用的 sharepoint 資料夾對應至您的專案。

## <a name="add-mapped-folders-to-a-project"></a>將對應資料夾新增至專案
 下列程式說明如何將兩個對應的資料夾加入至視覺 web 元件專案。 若要開始，請建立視覺 web 元件專案。

#### <a name="to-add-mapped-folders-to-a-project"></a>將對應資料夾新增至專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual Basic** ] 或 [ **Visual c #** ] 節點，展開 [ **Office/SharePoint** ] 節點，然後選擇 [ **SharePoint 方案** ] 節點。

3. 在專案範本清單中，選擇 [ **SharePoint 2013 視覺網頁元件** ] 範本。

4. 在 [ **名稱** ] 方塊中，輸入 **TestProject1**，然後選擇 [ **確定]** 按鈕。

5. 在 [ **SharePoint 自訂] 嚮導** 中，選擇 [ **完成]** 按鈕以保留預設設定。

6. 在 **方案總管** 中，選擇 [專案] 節點，然後在功能表列上選擇 [**專案**  >  **加入 SharePoint] 的 [影像] 對應資料夾**。

     名為「 **影像** 」的資料夾會出現在您的專案中，並包含名為 TestProject1 的子資料夾。 這個對應的資料夾將包含視覺 web 元件專案的影像。

7. 在 [**方案總管** 中，選擇專案節點，然後在功能表列上選擇 [**專案**  >  **加入 sharepoint 對應資料夾**]，以顯示 [**新增 sharepoint 對應資料夾**] 對話方塊。

8. 在可供對應之資料夾的樹狀檢視中，選擇 [ **資源** ] 資料夾，然後選擇 [ **確定]** 按鈕。

     名為 **資源** 的資料夾會出現在您的專案中。 此資料夾可以儲存像是字串資源檔的專案。 子資料夾有助於組織對應資料夾的內容，但是當您使用 [ **加入 SharePoint 對應資料夾** ] 命令加入對應資料夾時，不會自動建立子資料夾。 若要新增子資料夾，請選擇 [**資源**] 資料夾，然後在功能表列上選擇 [**專案**  >  **新資料夾**]。

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>變更對應資料夾的部署位置
 根據預設，對應的資料夾會加入至相對於權杖所代表之 SharePoint 根安裝路徑的特定位置 \<SharePointRoot> 。 不過，您可以變更對應資料夾的 [ **部署位置** ] 屬性來變更這個位置。 每個對應的資料夾都有自己的 **部署位置** 屬性。

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>變更對應資料夾的部署位置

1. 在您稍早建立的專案中，選擇對應資料夾。

2. 在 [**屬性**] 視窗中，選擇 [**部署位置**] 屬性上的省略號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕。

3. 在 [ **加入 SharePoint 對應資料夾** ] 對話方塊中，流覽至您要對應資料夾指向的資料夾。

4. 選擇節點，然後選擇 [ **確定]** 按鈕。

## <a name="rename-or-remove-mapped-folders"></a>重新命名或移除對應的資料夾

#### <a name="to-rename-or-remove-a-mapped-folder"></a>重新命名或移除對應的資料夾

1. 在您稍早建立的專案中，選擇對應資料夾。

2. 若要重新命名對應的資料夾，請開啟其快捷方式功能表，選擇 [ **重新命名**]，輸入新名稱，然後選擇 enter 鍵。

     或者，您可以選擇要重新命名的對應資料夾，開啟 [ **屬性** ] 視窗，然後將 [ **資料夾名稱** ] 屬性的值設定為新的名稱。

3. 若要從專案中移除對應的資料夾，請開啟其快捷方式功能表，選擇 [ **刪除**]，然後選擇對話方塊中的 [ **確定]** 按鈕以確認移除。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
