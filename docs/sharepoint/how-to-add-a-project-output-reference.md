---
title: HOW TO：加入專案輸出參考 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2ae3965647416d7a8e11cf0ea5e24cef1e54a09b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967249"
---
# <a name="how-to-add-a-project-output-reference"></a>HOW TO：加入專案輸出參考
  若要部署到 SharePoint 的非 SharePoint 專案的組件 （或 Silverlight 專案中的.xap 檔案），請將他們新增為專案輸出參考。

 此程序會建立兩個專案之間的方案組建相依性。 SharePoint 專案是建置和部署之前建置專案輸出參考相關聯的專案。

### <a name="to-add-a-project-output-reference"></a>若要加入專案輸出參考

1. 載入包含至少一個 SharePoint 專案和一個非 SharePoint 專案的方案。

2. 在 [**方案總管] 中**，選擇 SharePoint 專案節點中的項目。

3. 在 [**屬性**] 視窗中，選擇**專案輸出參考**屬性，然後選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP。NET Mobile 設計工具橢圓形")) 旁邊的按鈕。

4. 在 [**專案輸出參考**對話方塊方塊中，選擇**新增**] 按鈕。

5. 在 [屬性] 窗格中，選擇箭號旁**部署類型**屬性，然後選擇適當的值所參考，例如非 SharePoint 項目的**ElementFile**。

6. 選擇箭號旁**專案名稱**，選擇非 SharePoint 專案項目名稱，然後選擇**確定** 按鈕。

## <a name="see-also"></a>另請參閱
- [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [如何：將控制項標記為安全控制項](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
