---
title: 命令放置指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bac09a361c885d866bf6a78e6fe7b49c246265ba
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511182"
---
# <a name="command-placement-guidelines"></a>命令放置指導方針
Visual Studio 整合式的開發環境 (IDE) 中的定位命令的最佳作法是根據命令集的大小而有所不同。 定義命令，並根據中的資訊位於 *.vsct*檔案。  
  
## <a name="best-practices-for-all-command-sets"></a>所有的命令集的最佳作法  
 每一組命令，請遵循這些指導方針：  
  
-   事先準備命令結構的圖表。 識別命令、 下拉式方塊、 命令群組與將用於多個位置的捷徑功能表。  
  
-   出現在相同群組中的命令應該與相關。  
  
-   群組包含一個命令可接受的。  
  
-   封裝應該新增至現有的 Visual Studio 功能表的許多命令。 相反地，它們應該建立功能表或子功能表，來裝載新的命令。  
  
-   當您暫停命令現有的功能表名稱的命令，讓它的目的是清除並不會混淆與現有的命令。  
  
## <a name="best-practices-for-small-command-sets"></a>小型的命令集的最佳作法  
 如果您正在開發的 VSPackage，有少數的命令，也請遵循這些指導方針：  
  
-   可能的話，請使用[父](../../extensibility/parent-element.md)命令、 下拉式方塊、 群組或子功能表將它放在適當的群組項目。  
  
-   將這些群組指派至 VSPackage 所顯示的功能表。  
  
-   必須是父系的子功能表或命令[群組](../../extensibility/group-element.md)項目。 將命令和子功能表指派給群組，然後將群組指派給父功能表。  
  
-   您可以將命令放在其他群組加[CommandPlacements](../../extensibility/commandplacements-element.md)的定義之後的命令，然後再將加入的項目區段`CommandPlacements`項目[CommandPlacement](../../extensibility/commandplacement-element.md)項目針對每個額外的群組。  
  
## <a name="best-practices-for-large-command-sets"></a>大型的命令集的最佳作法  
 如果 VSPackage 必須將出現在多個內容中的許多命令，也請遵循這些指導方針：  
  
-   請功能表、 群組和自我的父代的命令。 也就是說，不要指派`Parent`的項目定義中的項目。  
  
-   使用`CommandPlacement`中的項目`CommandPlacements`項目在其父功能表和群組中放入功能表、 群組和命令的區段。  
  
-   在 [`CommandPlacements`項目] 區段中，填入指定的功能表或群組的項目應該是彼此相鄰。 這有助於提高可讀性，並使`Priority`更輕鬆地判斷的排名。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio 命令表檔案 (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)