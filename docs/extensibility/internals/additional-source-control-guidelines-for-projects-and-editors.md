---
title: 專案和編輯的其他原始程式碼管理指南 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710113"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>專案與編輯器的其他原始碼管理指南
專案和編輯應遵守許多準則來支援原始程式碼管理。

## <a name="guidelines"></a>指導方針
 您的項目或編輯器還應執行以下操作來支援原始碼管理:

|區域|隨附此逐步解說的專案|編輯器|詳細資料|
|----------|-------------|------------|-------------|
|檔案的私人複本|X||環境支援檔的私人副本。 也就是說,在專案中登記的每個人都有自己/她該專案中檔的私人副本。|
|ANSI/Unicode 持久性|X|X|如果編寫持久性代碼,請在 ANSI 窗體中保留檔,因為大多數原始程式碼控制程式當前不支援 Unicode。|
|列舉檔案|X||項目必須包含其中所有檔的特定清單,並且必須能夠枚舉使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>或 (VSH_PROPID_First_Child/Next_Sibling)的檔案清單。 專案還應通過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>實現公開專案名稱,並通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>實現 支援名稱查找(包括特殊檔)。|
|文字格式|X|X|如果可能,檔應採用文本格式,以支援合併不同版本。 以後不能將不是文本格式的檔與其他版本的文件合併。 偏好設定文字格式是 XML。|
|基於參考|X||原始程式碼管理中很容易支援基於引用的專案。 但是,只要專案可以按需生成其檔的清單,無論磁碟上是否存在這些檔,原始程式碼管理也會支援基於目錄的專案。 從原始程式碼管理打開專案時,專案檔首先在其任何檔之前被下拉。|
|以可預測的順序持久化物件和屬性|X|X|以可預測的順序(如字母順序)保留檔,以方便合併。|
|重新載入|X|X|當磁碟上的檔發生更改時,編輯器必須能夠重新載入它。 當您參與原始程式碼管理時,環境將透過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實現 來重新載入資料。 最困難的重新載入案例是在調用 IVsQueryEditQuerySave:<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和正在處理資訊時發生簽出時。 但是,重新載入代碼必須能夠在此情況下運行。<br /><br /> 環境會自動重新載入專案檔。 但是,如果專案具有嵌套<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>層次結構,則必須實現,以支援重新載入嵌套專案檔。|

## <a name="see-also"></a>另請參閱
- [支援原始碼管理](../../extensibility/internals/supporting-source-control.md)
