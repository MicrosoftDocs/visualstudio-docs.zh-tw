---
title: 按鍵繫結關係項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77fb94e702615d0d27ce2587c034000f6c4b3e3d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905099"
---
# <a name="keybinding-element"></a>KeyBinding 元素
按鍵繫結關係項目會指定命令的鍵盤快速鍵。  
  
 命令可以有與其相關聯的單一和雙重金鑰的連結。 單一索引鍵繫結的範例**Ctrl**+**S**如**儲存**命令。 雙重金鑰的繫結需要兩個連續的按鍵組合來觸發命令。 雙重金鑰繫結的範例<strong>Ctrl*+</strong>K<strong>，</strong>Ctrl<strong>+</strong>K** 若要設定書籤。  
  
## <a name="syntax"></a>語法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。|  
|id|必要。|  
|編輯器|必要。 編輯器 GUID 表示會使用此鍵盤快速鍵的編輯內容。 全域的繫結範圍值是"guidVSStd97 」。|  
|key1|必要。 有效值包括所有可輸入的英數字元，以及兩位數的十六進位值前面加上 0x 並[VK_constants](/windows/desktop/inputdev/virtual-key-codes)。|  
|mod1|選擇性。 任何組合**Ctrl**， **Alt**，並**Shift**以空格分隔的。|  
|key2|選擇性。 有效值包括所有可輸入的英數字元，以及兩位數的十六進位值前面加上 0x 並[VK_constants](/windows/desktop/inputdev/virtual-key-codes)。|  
|mod2|選擇性。 任何組合**Ctrl**， **Alt**，並**Shift**以空格分隔的。|  
|模擬器|選擇性。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父代||  
|註釋||  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[KeyBindings 元素](../extensibility/keybindings-element.md)|群組按鍵繫結關係項目和其他按鍵繫結關係分組。|  
  
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
 [KeyBindings 元素](../extensibility/keybindings-element.md)   
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
