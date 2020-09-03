---
title: KeyBinding 元素 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180320"
---
# <a name="keybinding-element"></a>KeyBinding 項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KeyBinding 元素會指定命令的鍵盤快速鍵。  
  
 命令可以有與它們相關聯的單一和雙重金鑰系結。 [ **儲存** ] 命令的單一按鍵系結範例是 CTRL + S。 雙重按鍵系結需要兩個連續的按鍵組合來觸發命令。 雙按鍵系結的範例是 CTRL + K、CTRL + K 來設定書簽。  
  
## <a name="syntax"></a>語法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。|  
|id|必要。|  
|編輯器|必要。 編輯器 GUID 會指出這個鍵盤快速鍵將使用的編輯內容。 全域系結範圍值為 "guidVSStd97"。|  
|key1|必要。 有效的值包括所有 typable 的英數位元，以及兩位數的十六進位值（前面加上0x 和 VK_constants）。|  
|mod1|選擇性。 CTRL、ALT 和 SHIFT 的任意組合（以空格分隔）。|  
|key2|選擇性。 有效的值包括所有 typable 的英數位元，以及兩位數的十六進位值（前面加上0x 和 VK_constants）。|  
|mod2|選擇性。 CTRL、ALT 和 SHIFT 的任意組合（以空格分隔）。|  
|模擬器|選擇性。|  
|條件|選擇性。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父系||  
|Annotation||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[KeyBindings 元素](../extensibility/keybindings-element.md)|群組 KeyBinding 元素和其他 Keybindings.json 群組。|  
  
## <a name="example"></a>範例  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Keybindings.json 元素](../extensibility/keybindings-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
