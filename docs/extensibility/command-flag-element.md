---
title: 命令旗標的項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 036b9658957b76b62e3a9b44b59e07700f276a32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107929"
---
# <a name="command-flag-element"></a>命令旗標的項目
修改其父項目。  
  
## <a name="syntax"></a>語法  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下節將說明有效的項目值。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|值|描述|  
|-----------|-----------------|  
|AllowParams|表示使用者可以輸入中的命令參數**命令**他們輸入命令的正式名稱時，視窗。<br /><br /> 適用於： `Button`|  
|AlwaysCreate|即使它沒有任何群組或按鈕時，會建立功能表。<br /><br /> 適用於： `Menu`|  
|CaseSensitive|使用者項目會區分大小寫。<br /><br /> 適用於： `Combo`|  
|CommandWellOnly|如果命令未出現在最上層功能表上，而且您想要使其可供其他殼層自訂，例如，為繫結至鍵盤快速鍵，請套用這個旗標。 VSPackage 安裝之後，您可以自訂這些命令開啟**選項**對話方塊，然後編輯下的命令位置**鍵盤環境**類別目錄。 這個旗標不會影響在快顯功能表、 工具列、 功能表控制器或子功能表上的位置。<br /><br /> 適用於： `Button`， `Combo`|  
|DefaultDisabled|根據預設，已停用命令如果未載入 VSPackage 實作它或`QueryStatus`尚未呼叫方法。<br /><br /> 適用於： `Button`， `Combo`|  
|DefaultDocked|依預設停駐。 這項設定不再適用於工具列，因為一律停駐。|  
|DefaultInvisible|根據預設，此命令是不可見，如果未載入 VSPackage 實作它或`QueryStatus`尚未呼叫方法。<br /><br /> 我們建議您合併這與`DynamicVisibility`旗標。<br /><br /> 適用於： `Button`， `Combo`， `Menu`|  
|DontCache|在開發環境並不會快取`QueryStatus`方法的結果，此命令。<br /><br /> 對於功能表，這會告訴功能表控制器不是用來快取的功能表項目文字。 功能表又包含動態項目或動態文字的項目時，請使用這個旗標。<br /><br /> 適用於： `Button`， `Menu`|  
|DynamicItemStart|表示動態清單的開頭。 這可讓環境，以建立清單，藉由連續呼叫`QueryStatus`直到傳回 OLECMDERR_E_UNSUPPORTED 旗標的清單項目上的方法。 這適用於項目，例如最近使用的 (MRU) 清單及視窗清單。<br /><br /> 適用於： `Button`|  
|DynamicVisibility|此命令的可見性可以透過變更`QueryStatus`方法或透過在內容中隨附的 GUID `VisibilityConstraints` > 一節。<br /><br /> 適用於功能表和工具視窗工具列，但不是會出現在主視窗的最上層工具列會出現的命令。 最上層工具列項目可以停用，但未隱藏，從傳回 OLECMDF_INVISIBLE 旗標時`QueryStatus`方法。 工具列會出現在工作視窗工具列的命令可以隱藏。<br /><br /> 在功能表上，此旗標也會指出，它應該會自動隱藏隱藏其所有成員時。 這個旗標通常會指派給子功能表，因為最上層功能表已經有這個行為。<br /><br /> 這個旗標應與結合`DefaultInvisible`旗標。<br /><br /> 適用於： `Button`， `Combo`， `Menu`|  
|篩選鍵|請參閱下的篩選鍵主題[下拉式項目](../extensibility/combo-element.md)。<br /><br /> 適用於： `Combo`|  
|FixMenuController|如果此命令位於功能表控制器，命令一律是預設值。也就被選取之功能表控制器按鈕本身時，會選取命令。 如果功能表控制站擁有`TextIsAnchorCommand`旗標集，功能表控制器也會採用其命令，從文字`FixMenuController`旗標。<br /><br /> 只能有一個命令，功能表控制器上的應該有`FixMenuController`旗標。 如果如此標示多個命令，功能表中的最後一個命令會變成預設命令。<br /><br /> 適用於： `Button`|  
|IconAndText|功能表和工具列上顯示的圖示和文字。<br /><br /> 適用於： `Button`， `Combo`， `Menu`|  
|NoAutoComplete|已停用自動完成功能。<br /><br /> 適用於： `Combo`|  
|NoButtonCustomize|不要讓使用者可以自訂此按鈕。<br /><br /> 適用於： `Button`， `Combo`|  
|NoKeyCustomize|請勿啟用鍵盤自訂。<br /><br /> 適用於： `Button`， `Combo`|  
|NoShowOnMenuController|如果此命令位於功能表控制器，命令不會出現在下拉式清單。<br /><br /> 適用於： `Button`|  
|NotInTBList|不會顯示在 可用工具列的清單。 這是僅適用於工具列功能表類型。<br /><br /> 適用於： `Menu`|  
|NoToolbarClose|使用者無法關閉工具列。 這是僅適用於工具列功能表類型。<br /><br /> 適用於： `Menu`|  
|Pict|只有圖示顯示在工具列上，但功能表上的文字。 如果未不指定任何圖示，顯示可點按的空白空間的工具列上。<br /><br /> 適用於： `Button`|  
|PostExec|可讓命令非封鎖。 在開發環境會延後執行，直到完成所有前置處理查詢。<br /><br /> 適用於： `Button`|  
|RouteToDocs|命令路由至使用中文件。<br /><br /> 適用於： `Button`|  
|StretchHorizontally|當設定這個旗標時，寬度會變成下拉式方塊的最小寬度，有在工具列上有足夠的空間，下拉式方塊會自動縮放以填滿可用空間。 發生這種情況的水平停駐工具列和工具列上的一個下拉式方塊可以使用旗標 （旗標會忽略第一個下拉式方塊以外的所有） 時，才可以。<br /><br /> 適用於： `Combo`|  
|TextMenuUseButton|使用`ButtonText`功能表的欄位。 預設欄位是`MenuText`如果有指定。<br /><br /> 適用於： `Button`|  
|文字變更|命令或功能表變更的文字可以在執行階段，通常透過`QueryStatus`方法。<br /><br /> 適用於： `Button`， `Menu`|  
|TextChangesButton|適用於： `Button`|  
|TextIsAnchorCommand|功能表控制器，功能表的文字會取自預設 （錨點） 命令。 錨定命令是選取或閂鎖的最後一個命令。 如果未設定此旗標，功能表控制器會使用它自己`MenuText`欄位。 不過，按一下功能表控制器仍會啟用選取的最後一個命令，從該控制器。<br /><br /> 我們建議您合併具有此旗標`TextChanges`旗標。<br /><br /> 這個旗標僅適用於類型的功能表 MenuController 或 MenuControllerLatched。<br /><br /> 適用於： `Menu`|  
|TextMenuCtrlUseMenu|使用`MenuText`功能表控制站上的欄位。 預設欄位是`ButtonText`。<br /><br /> 適用於： `Button`|  
|TextMenuUseButton|使用`ButtonText`功能表的欄位。 預設欄位是`MenuText`如果有指定。<br /><br /> 適用於： `Button`|  
|TextOnly|即使未指定圖示，請只會將文字顯示工具列或功能表上，但無圖示上。<br /><br /> 適用於： `Button`|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Buttons 元素](../extensibility/buttons-element.md)|提供的群組[按鈕項目](../extensibility/button-element.md)項目。|  
|[Menus 元素](../extensibility/menus-element.md)|定義所有實作 VSPackage 的功能表。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)