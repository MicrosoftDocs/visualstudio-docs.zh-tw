---
title: 可見性項目元素 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698155"
---
# <a name="visibilityitem-element"></a>可見性項目元素
該`VisibilityItem`元素確定命令和工具列的靜態可見性。 每個條目標識命令或功能表,以及關聯的命令 UI 上下文。 Visual Studio 檢測命令、功能表和工具列及其可見性,而無需載入定義它們的 VS 包。 IDE<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>使用 方法確定命令 UI 上下文是否處於活動狀態。

 載入 VSPackage 後,Visual Studio 希望命令可見性由 VSPackage 而不是 確定`VisibilityItem`。 要確定命令的可見性,可以實現<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>事件處理程式<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>或 方法,具體取決於實現命令的方式。

 僅當關聯的上下文處於活動狀態時,才會`VisibilityItem`顯示具有元素的命令或功能表。 通過為每個命令上下文組合包含一個條目,可以將單個命令、功能表或工具列與一個或多個命令 UI 上下文相關聯。 如果命令或功能表與多個命令 UI 上下文相關聯,則當任何關聯的命令 UI 上下文處於活動狀態時,命令或功能表可見。

 該`VisibilityItem`元素僅適用於命令、功能表和工具列,不適用於組。 每當其父功能表處於活動狀態時,沒有`VisibilityItem`相關元素的元素都會可見。

## <a name="syntax"></a>語法

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|guid|必要。 GUID/ID 命令識別碼的 GUID。|
|id|必要。 GUID/ID 命令識別碼的識別碼。|
|內容|必要。 命令可見的 UI 上下文。|
|條件|選擇性。 請參考[條件屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|

### <a name="child-elements"></a>子元素
 None

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[可見性限制元素](../extensibility/visibilityconstraints-element.md)|該`VisibilityConstraints`元素確定命令組和工具列的靜態可見性。|

## <a name="remarks"></a>備註
 標準視覺化工作室 UI 上下文在 Visual *Studio SDK 安裝路徑*[VisualStudio 整合式<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids><xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>]公共_Inc_vsshlids.h 檔中以及和類中定義。 <xref:Microsoft.VisualStudio.VSConstants>類中定義了一組更完整的 UI 上下文。

## <a name="example"></a>範例

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [可見性限制元素](../extensibility/visibilityconstraints-element.md)
- [視覺化工作室命令表 (.Vsct) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
