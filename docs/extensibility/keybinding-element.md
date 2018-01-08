---
title: "按鍵繫結關係的項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2019a34e55148007cd75df12212bd4b0a897159c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="keybinding-element"></a>按鍵繫結關係的項目
按鍵繫結關係項目會指定命令的鍵盤快速鍵。  
  
 命令可以有單一和雙重按鍵繫結與其相關聯。 單一索引鍵繫結的範例是 CTRL + S**儲存**命令。 雙重按鍵繫結需要兩個連續的按鍵組合來觸發命令。 雙重繫結的範例是 CTRL + K、 CTRL + K 設定書籤。  
  
## <a name="syntax"></a>語法  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|Guid|必要。|  
|id|必要。|  
|編輯器|必要。 編輯器 GUID 表示會使用此鍵盤快速鍵的編輯內容。 全域的繫結範圍的值是"guidVSStd97"。|  
|key1|必要。 有效值包括所有可輸入的英數字元，以及兩位數的十六進位值前面加上 0x 和[VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx)。|  
|mod1|選擇性。 CTRL、 ALT 和 shift 鍵，以空格分隔的任何組合。|  
|key2|選擇性。 有效值包括所有可輸入的英數字元，以及兩位數的十六進位值前面加上 0x 和[VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx)。|  
|mod2|選擇性。 CTRL、 ALT 和 shift 鍵，以空格分隔的任何組合。|  
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
|[KeyBindings 元素](../extensibility/keybindings-element.md)|群組 KeyBinding 項目和其他按鍵組合群組。|  
  
## <a name="example"></a>範例  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>請參閱  
 [金鑰繫結項目](../extensibility/keybindings-element.md)   
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
