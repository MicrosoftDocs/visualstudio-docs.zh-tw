---
title: 定義元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712266"
---
# <a name="define-element"></a>定義項目
定義符號名稱和值對。 此符號可以通過條件屬性計算。 有關詳細資訊,請參閱[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。 另請參考[符號元素](../extensibility/symbols-element.md)。

## <a name="syntax"></a>語法

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|NAME|必要。 符號的名稱:<br /><br /> 名稱="模式"|
|value|必要。 符號的值:<br /><br /> 值="標準"|
|條件|選擇性。 有關詳細資訊,請參閱[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[指令表元素](../extensibility/commandtable-element.md)|定義表示 VS 套件向整合式開發環境 (IDE) 提供的命令的所有元素。 例如,功能表項、功能表、工具列和組合框。|

## <a name="example"></a>範例

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>另請參閱
- [視覺化工作室指令表 (.vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
