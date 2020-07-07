---
title: 如何：新增資源檔 |Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015185"
---
# <a name="how-to-add-a-resource-file"></a>如何：新增資源檔
  用於新增資源檔的命令位於 [方案] 節點的快捷方式功能表和方案總管中的功能節點。 如需詳細資訊，請參閱[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)。

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>將全域資源檔加入至 SharePoint 方案

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，開啟 SharePoint 方案。

2. 在**方案總管**中，選擇 SharePoint 專案節點，然後在功能表列上，選擇 [**專案**] [新增] [  >  **新專案**]。

3. 在 [**加入新專案**] 對話方塊中，選擇 [**全域資源檔**] 範本，然後選擇 [**加入**] 按鈕。

   > [!NOTE]
   > [全域資源檔] 專案專案範本只會在選取 SharePoint 專案專案時出現。

4. 在 [**新增資源**] 對話方塊中，選擇資源檔的文化特性，例如 [英文（美國）]。

    此步驟會將全域資源檔新增至您的方案，格式為 Resource_x_**。**<em>文化</em>特性<strong>。</strong>resx，例如， *Resource1*。

5. 當**資源編輯器**在中開啟時 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，將資源新增至資源檔。

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>若要將功能資源檔加入至 SharePoint 功能

1. 如果 SharePoint 方案尚未在中開啟 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，請開啟方案。

2. 在**方案總管**中，開啟 [**功能**] 節點底下功能名稱的快捷方式功能表，然後選擇 [**加入功能資源**]。

     此步驟會將資源檔新增至功能，格式為_ResourceFileName_**。**_culture_**.resx**，例如，Feature1 （*英文*）。

3. 當**資源編輯器**在中開啟時 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，將資源新增至資源檔。

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
