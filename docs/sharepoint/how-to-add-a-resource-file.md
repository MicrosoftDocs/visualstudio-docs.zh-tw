---
title: 如何：新增資源檔 |Microsoft Docs
description: 在 Visual Studio 中，使用方案節點的快捷方式功能表上的命令，以及方案總管中的功能節點，來新增資源檔。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 22b5638f7251b34c74da348e55e755cd27132aff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934841"
---
# <a name="how-to-add-a-resource-file"></a>如何：新增資源檔
  新增資源檔的命令位於 [方案] 節點的快捷方式功能表和方案總管中的功能節點。 如需詳細資訊，請參閱 [當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>將全域資源檔加入至 SharePoint 方案

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，開啟 SharePoint 方案。

2. 在 **方案總管** 中，選擇 SharePoint 專案節點，然後在功能表列上選擇 [**專案**  >  **加入新專案**]。

3. 在 [ **加入新專案** ] 對話方塊中，選擇 [ **全域資源檔** ] 範本，然後選擇 [ **加入** ] 按鈕。

   > [!NOTE]
   > 只有在選取 SharePoint 專案專案時，才會顯示全域資源檔專案專案範本。

4. 在 [ **新增資源** ] 對話方塊中，選擇資源檔的文化特性，例如 [英文 (美國) 。

    此步驟會以 Resource_x_ 的格式，將全域資源檔加入至您的方案 **。**<em>文化</em>特性 <strong>。</strong>resx，例如， *Resource1*。

5. 當 **資源編輯器** 在中開啟時 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，請將資源新增至資源檔。

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>將功能資源檔新增至 SharePoint 功能

1. 如果 SharePoint 方案尚未在中開啟 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，請開啟方案。

2. 在 **方案總管** 中，開啟 [ **功能** ] 節點下之功能名稱的快捷方式功能表，然後選擇 [ **加入功能資源**]。

     此步驟會將資源檔新增至功能，格式為 _ResourceFileName_**。**_culture_**，例如**，Feature1，例如： *en-us*。

3. 當 **資源編輯器** 在中開啟時 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，請將資源新增至資源檔。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
