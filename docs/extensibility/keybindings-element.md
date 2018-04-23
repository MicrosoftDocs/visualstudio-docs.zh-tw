---
title: 金鑰繫結項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91a5fd99216e712e567d4543f3f29dc2b6b21aa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="keybindings-element"></a>金鑰繫結項目
金鑰繫結項目群組 KeyBinding 項目和其他按鍵組合群組。  
  
## <a name="syntax"></a>語法  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[KeyBinding 元素](../extensibility/keybinding-element.md)|指定命令的鍵盤快速鍵。|  
|[按鍵組合](../extensibility/keybindings-element.md)|群組 KeyBinding 項目和其他按鍵組合群組。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定義代表命令的所有項目。|  
  
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
 [按鍵繫結關係的項目](../extensibility/keybinding-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)