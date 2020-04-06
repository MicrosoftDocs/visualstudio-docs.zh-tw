---
title: 鍵繫結元素 ( T) :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703150"
---
# <a name="keybinding-element"></a>鍵繫結元素
KeyBinding 元素指定命令的鍵盤快捷方式。

 命令可以同時具有與其關聯的單鍵和雙密鑰綁定。 單個鍵繫執行的範例是 **「儲存**」命令的**Ctrl**+**S。** 雙鍵綁定需要兩個連續的鍵組合才能觸發命令。 雙鍵繫參數的範例是<strong>Ctrl*+</strong>K<strong>,</strong>Ctrl<strong>+</strong>K*= 來設定書籤。

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
|編輯器|必要。 編輯器 GUID 指示此鍵盤快捷方式將處於活動狀態的編輯上下文。 全域綁定範圍值為「guidVSStd97」。。|
|key1|必要。 有效值包括所有可鍵入的字母數位,以及前面以 0x 和[VK_constants](/windows/desktop/inputdev/virtual-key-codes)開頭的兩位十進位值。|
|mod1|選擇性。 **Ctrl、Alt****Alt**和**Shift**的任意組合由空間分隔。|
|key2|選擇性。 有效值包括所有可鍵入的字母數位,以及前面以 0x 和[VK_constants](/windows/desktop/inputdev/virtual-key-codes)開頭的兩位十進位值。|
|mod2|選擇性。 **Ctrl、Alt****Alt**和**Shift**的任意組合由空間分隔。|
|模擬器|選擇性。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|父系||
|Annotation||

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[鍵繫結元素](../extensibility/keybindings-element.md)|對鍵綁定元素和其他鍵綁定分組進行分組。|

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
- [鍵繫結元素](../extensibility/keybindings-element.md)
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
