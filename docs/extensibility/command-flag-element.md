---
title: 命令標誌元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649374"
---
# <a name="command-flag-eelement"></a>命令標誌 Eelement
修改其父元素。

## <a name="syntax"></a>語法

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>屬性和元素
 以下部分介紹有效的元素值。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|值|描述|
|-----------|-----------------|
|允許帕姆斯|指示用戶可以在**命令視窗中輸入**命令參數,當他們鍵入命令的規範名稱時。<br /><br /> 合法:`Button`|
|始終建立|即使功能表沒有組或按鈕,也會創建功能表。<br /><br /> 合法:`Menu`|
|CaseSensitive|使用者項目分大小寫。<br /><br /> 合法:`Combo`|
|命令井只|如果命令未顯示在頂級選單上,並且您希望使其可用於其他 shell 自訂(例如,將其綁定到鍵盤快捷方式),請應用此標誌。 安裝 VSPackage 後,可以透過開啟 **「選項」** 對話框,然後在 **「鍵盤環境**」類別下編輯命令放置來自定義這些命令。 此標誌不會影響在快捷功能表、工具列、功能表控制器或子選單上的位置。<br /><br /> 適用於: `Button`, ,`Combo`|
|預設關閉|預設情況下,如果未載入實現該命令的 VSPackage 或未調用該`QueryStatus`方法, 則禁用該命令。<br /><br /> 適用於: `Button`, ,`Combo`|
|預設已載|默認情況下停靠。 此設置不再適用於工具列,因為它們始終停靠。|
|預設不可見|預設情況下,如果未載入實現該命令的 VSPackage 或未調用該`QueryStatus`方法, 則該命令不可見。<br /><br /> 我們建議您將此與`DynamicVisibility`標誌合併。<br /><br /> 適用於: `Button` `Combo`、 、 、 、 、 、 、 、 、 、 、 、 、`Menu`|
|唐特卡奇|開發環境不會緩存此命令`QueryStatus`的方法結果。<br /><br /> 對於功能表,這告訴菜單控制器不要緩存其功能表項的文本。 當選單包含動態項或具有動態文本的項時,使用此標誌。<br /><br /> 適用於: `Button`, ,`Menu`|
|動態項目啟動|指示動態清單的開頭。 這使環境能夠生成清單,方法是在返回OLECMDERR_E_UNSUPPORTED標誌之前`QueryStatus`在清單項上連續調用該方法。 這適用於最近使用 (MRU) 列表和視窗列表等項。<br /><br /> 合法:`Button`|
|動態可見度|命令的可見性可以`QueryStatus`通過 方法`VisibilityConstraints`或通過 本節中包含的上下文 GUID 進行更改。<br /><br /> 應用於顯示在功能表和工具視窗工具列上的命令,但不適用於顯示在主視窗中的頂級工具列。 當從`QueryStatus`方法返回OLECMDF_INVISIBLE標誌時,可以禁用但無法隱藏頂級工具欄項。 可以隱藏出現在工具視窗工具列上的工具列命令。<br /><br /> 在功能表上,此標誌還指示在隱藏所有成員時自動隱藏它。 此標誌通常分配給子功能表,因為頂級功能表已具有此行為。<br /><br /> 此標誌應與`DefaultInvisible`標誌組合。<br /><br /> 適用於: `Button` `Combo`、 、 、 、 、 、 、 、 、 、 、 、 、`Menu`|
|篩選器鍵|請參閱[組合元素](../extensibility/combo-element.md)下的篩選鍵主題。<br /><br /> 合法:`Combo`|
|修復選單控制器|如果此命令位於功能表控制器上,則該命令始終為預設值;如果此命令位於菜單控制器上,則該命令始終為預設命令。也就是說,每當選擇功能表控制器按鈕本身時,都會選擇該命令。 如果選單控制器設定了`TextIsAnchorCommand`標誌,則功能表控制器也會從`FixMenuController`具有 標誌的命令中獲取其文本。<br /><br /> 選單控制器上只有一個指令應具有標誌`FixMenuController`。 如果多個命令被如此標記,則功能表中的最後一個命令將成為預設命令。<br /><br /> 合法:`Button`|
|圖示與文字|在功能表和工具列上顯示圖示和文本。<br /><br /> 適用於: `Button` `Combo`、 、 、 、 、 、 、 、 、 、 、 、 、`Menu`|
|沒有自動完成|自動完成功能已禁用。<br /><br /> 合法:`Combo`|
|沒有按鈕|不要讓使用者自定義此按鈕。<br /><br /> 適用於: `Button`, ,`Combo`|
|NoKey 客製|不要啟用鍵盤自定義。<br /><br /> 適用於: `Button`, ,`Combo`|
|諾秀翁選單控制器|如果此命令位於功能表控制器上,則該命令不會顯示在下拉清單中。<br /><br /> 合法:`Button`|
|NOTTBlist|不顯示在可用工具列清單中。 這僅適用於工具列功能表類型。<br /><br /> 合法:`Menu`|
|沒有工具列關閉|使用者無法關閉工具列。 這僅適用於工具列功能表類型。<br /><br /> 合法:`Menu`|
|皮克特|僅顯示工具列上的圖示,但僅顯示功能表上的文本。 如果未指定圖示,請在工具列上顯示可按下的空白。<br /><br /> 合法:`Button`|
|PostExec|使命令不阻塞。 開發環境將延遲執行,直到完成所有預處理查詢。<br /><br /> 合法:`Button`|
|路由到文件|該命令路由到活動文檔。<br /><br /> 合法:`Button`|
|水平拉伸|設置此標誌時,寬度將成為組合框的最小寬度,如果工具列上有空間,組合框將拉伸以填充可用空間。 僅當工具列水準停靠時,並且工具列上只有一個組合框可以使用標誌(除第一個組合框外,所有組合框上都忽略該標誌),才會發生這種情況。<br /><br /> 合法:`Combo`|
|文字變更|指令或選單文字可以在執行時更改,通常透過方法`QueryStatus`。<br /><br /> 適用於: `Button`, ,`Menu`|
|文字變更按鈕|合法:`Button`|
|文字 Isanchor 命令|對於功能表控制器,功能表的文本取自預設(錨點)命令。 錨點命令是選擇或鎖定的最後一個命令。 如果未設置此標誌,功能表控制器將使用其自己的`MenuText`欄位。 但是,單擊功能表控制器仍啟用該控制器的最後一個選定命令。<br /><br /> 我們建議您將此標誌與`TextChanges`標誌合併。<br /><br /> 此標誌僅適用於類型功能表控制器或功能表控制器鎖定的功能表。<br /><br /> 合法:`Menu`|
|文字選單Ctrluse選單|使用功能表`MenuText`控制器上的欄位。 預設欄位為`ButtonText`。<br /><br /> 合法:`Button`|
|文字選單使用按鈕|對`ButtonText`功能表使用該欄位。 預設欄位是`MenuText`指定欄位。<br /><br /> 合法:`Button`|
|只有文字|僅在工具列或功能表上顯示文本,但即使指定了圖示,也沒有圖示。<br /><br /> 合法:`Button`|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[按鈕項目](../extensibility/buttons-element.md)|為 Button[元素元素](../extensibility/button-element.md)提供群組。|
|[選單元素](../extensibility/menus-element.md)|定義 VSPackage 實現的所有功能表。|

## <a name="see-also"></a>另請參閱
- [視覺化工作室命令表 (.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
