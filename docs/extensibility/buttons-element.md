---
title: 按鈕元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64ac5621093f30af28ade0817906b767231e4ee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739926"
---
# <a name="buttons-element"></a>按鈕項目
對[表示](../extensibility/button-element.md)單個命令的按鈕元素進行分組。

## <a name="syntax"></a>語法

```
<Buttons>
  <Button>... </Button>
  <Button>... </Button>
</Buttons>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[按鈕項目](../extensibility/buttons-element.md)|對按鈕元素進行分組。|
|[按鈕項目](../extensibility/button-element.md)|定義用戶可以與之交互的命令。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令元素](../extensibility/commands-element.md)|表示 VSPackage 工具列上的命令集合。|

## <a name="example"></a>範例

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>另請參閱
- [VS 套件如何新增使用者介面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [命令、選單和工具列](../extensibility/internals/commands-menus-and-toolbars.md)
