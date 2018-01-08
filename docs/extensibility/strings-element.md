---
title: "字串項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61d6498cafaf97033864bc31d55c257c9a3a564f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="strings-element"></a>字串的項目
字串元素必須包含至少一個**ButtonText**子項目。 所有其他子項目是選擇性的。 無效的 XML 字元，例如 '&' 和 '<' 必須編碼為實體 ('&amp;'和'&lt;' 等)。  
  
 文字字串中的以連字號指定命令的鍵盤快速鍵。  
  
## <a name="syntax"></a>語法  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|語言|選擇性。 語言 ="。"。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|ButtonText|這個欄位和命令定義中的五個下列文字欄位可讓您指定各種功能表中出現的文字。 根據預設，`ButtonText`欄位會出現在功能表控制器。 `ButtonText`欄位也會成為預設值，如果是空白的其他文字欄位。 `ButtonText`欄位不可為空白，即使指定的文字欄位。|  
|ToolTipText|`ToolTipText`欄位指定功能表項目的工具提示中顯示的文字。<br /><br /> 如果`ToolTipText`欄位是空白的`ButtonText`欄位使用。|  
|MenuText|`MenuText`欄位會指定是否在主功能表工具列上，在快顯功能表中，或在子功能表中，會將命令顯示的文字。 如果`MenuText`欄位空白，會使用整合式的開發環境 (IDE)`ButtonText`欄位。 `MenuText`欄位也可用來當地語系化。<br /><br /> 對於快顯功能表`MenuText`欄位會顯示在快顯功能表工具列中，可自訂的捷徑功能表，在 IDE 中的名稱。 因此，會在您命名您的快顯功能表; 特定例如，使用 「 小工具封裝捷徑功能表 」 而不是 「 捷徑 」。<br /><br /> 如果`MenuText`未指定欄位，`ButtonText`欄位使用。|  
|CommandName|`CommandName`欄位指定鍵盤類別目錄中所顯示的文字**命令**索引標籤中**自訂**對話方塊 (按一下**自訂**上**工具**功能表)。|  
|canonicalName|英文`CanonicalName`欄位在英文中可輸入的文字中指定的命令名稱**命令**視窗中執行的功能表項目。 IDE 會刪除任何不是字母、 數字、 底線或內嵌的句號的字元。 此文字然後要串連到`ButtonText`欄位來定義命令。 例如，**新專案**上**檔案**功能表會變成 File.NewProject 命令。<br /><br /> 如果英文`CanonicalName`欄位沒有指定，則 IDE 使用`ButtonText`欄位和帶狀線所有除了字母、 數字、 底線和內嵌的句號。 例如，則按鈕文字"& 定義命令 …"會成為的 DefineCommands，移除連字號、 空格和省略符號。<br /><br /> 如果`TextChanges`指定旗標和命令的文字會變更，所辨識的對應命令**命令**視窗不會變更; 它會保留原始的標準格式`ButtonText`或英文`CanonicalName`欄位。|  
|LocCanonicalName|`LocCanonicalName`欄位運作方式完全相同的英文`CanonicalName`欄位但可讓指定當地語系化的命令文字。 您可以指定兩個標準欄位。 因為 IDE 只會剖析輸入中的文字**命令**視窗，並將它與英文與非英文文字的命令可以是相同的命令相關聯。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Button 元素](../extensibility/button-element.md)|定義使用者可以與之互動的項目。|  
|[Menu 元素](../extensibility/menu-element.md)|定義單一功能表項目。|  
|[Combo 元素](../extensibility/combo-element.md)|定義了出現在下拉式方塊中的命令。|  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)