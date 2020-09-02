---
title: 如何：加入專案輸出參考 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bea0f39ae161d8b695f872cb634c35d0cb205c91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016758"
---
# <a name="how-to-add-a-project-output-reference"></a>如何：加入專案輸出參考
  若要在 Silverlight 專案中部署非 SharePoint 專案元件 (或 .xap 檔案) 至 SharePoint，請將它們新增為專案輸出參考。

 這項程式會建立兩個專案之間的方案組建相依性。 與專案輸出參考相關聯的專案，會在建立和部署 SharePoint 專案之前建立。

### <a name="to-add-a-project-output-reference"></a>若要加入專案輸出參考

1. 載入至少包含一個 SharePoint 專案和一個非 SharePoint 專案的方案。

2. 在 **方案總管**中，選擇 SharePoint 專案節點中的專案。

3. 在 [ **屬性** ] 視窗中，選擇 [ **專案輸出參考** ] 屬性，然後選擇旁邊的省略號 (![ASP.NET Mobile Designer 橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕。

4. 在 [ **專案輸出參考** ] 對話方塊中，選擇 [ **加入** ] 按鈕。

5. 在 [屬性] 窗格中，選擇 [ **部署類型** ] 屬性旁邊的箭號，然後為您所參考的非 SharePoint 專案選擇適當的值，例如 [ **ElementFile**]。

6. 選擇 [ **專案名稱**] 旁邊的箭號，選擇非 SharePoint 專案專案的名稱，然後選擇 [ **確定]** 按鈕。

## <a name="see-also"></a>另請參閱
- [提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [如何：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
