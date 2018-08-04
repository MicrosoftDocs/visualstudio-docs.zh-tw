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
ms.openlocfilehash: a199a805493b0b9ac9ae6e75cec322c74a99987e
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511570"
---
# <a name="keybinding-element"></a>KeyBinding 項目
按鍵繫結關係項目會指定命令的鍵盤快速鍵。  
  
 命令可以有與其相關聯的單一和雙重金鑰的連結。 單一索引鍵繫結的範例是 CTRL + S**儲存**命令。 雙重金鑰的繫結需要兩個連續的按鍵組合來觸發命令。 雙重金鑰繫結的範例是 CTRL + K、 CTRL + K，若要設定書籤。  
  
## <a name="syntax"></a>語法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。|  
|id|必要。|  
|編輯器|必要。 編輯器 GUID 表示會使用此鍵盤快速鍵的編輯內容。 全域的繫結範圍值是"guidVSStd97 」。|  
|key1|必要。 有效值包括所有可輸入的英數字元，以及兩位數的十六進位值前面加上 0x 並[VK_constants](/windows/desktop/inputdev/virtual-key-codes)。|  
|mod1|選擇性。 CTRL、 ALT 和 shift 鍵以空格分隔的任何組合。|  
|key2|選擇性。 有效值包括所有可輸入的英數字元，以及兩位數的十六進位值前面加上 0x 並[VK_constants](/windows/desktop/inputdev/virtual-key-codes)。|  
|mod2|選擇性。 CTRL、 ALT 和 shift 鍵以空格分隔的任何組合。|  
|模擬器|選擇性。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|父代||  
|註釋||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
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
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
