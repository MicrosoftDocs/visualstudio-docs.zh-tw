---
title: 專案和編輯器的原始檔控制指導方針
description: 瞭解專案和編輯器為了支援原始檔控制，應遵守的指導方針。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 688c7de73c1a935ed6f7a30c6d956c7db97bdc6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906124"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>專案和編輯器的其他原始檔控制指導方針
為了支援原始檔控制，專案和編輯器必須遵守一些指導方針。

## <a name="guidelines"></a>指導方針
 您的專案或編輯器也應該執行下列作業，以支援原始檔控制：

|區域|Project|編輯器|詳細資料|
|----------|-------------|------------|-------------|
|檔案的私用複本|X||環境支援檔的私用複本。 也就是說，在專案中登錄的每個人都有自己的私用該專案中的檔案複本。|
|ANSI/Unicode 持續性|X|X|如果您撰寫持續性程式碼，請將檔案保存在 ANSI 格式中，因為大部分的原始檔控制程式目前不支援 Unicode。|
|列舉檔案|X||專案必須包含其內所有檔案的特定清單，而且必須能夠使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling) 來列舉檔案清單。 專案也應該透過其執行來公開專案名稱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> ，並支援名稱查閱 (包括透過其執行) 的特殊檔案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> 。|
|文字格式|X|X|可能的話，檔案應該是文字格式，以支援合併不同的版本。 不是文字格式的檔案，稍後就無法與其他版本的檔案合併。 慣用的文字格式為 XML。|
|參考型|X||原始檔控制中可立即支援參考型專案。 不過，原始檔控制也支援目錄型專案，只要專案可以視需要產生其檔案清單，無論這些檔案是否存在於磁片上。 從原始檔控制開啟專案時，專案檔會在其任何檔案之前先關閉。|
|以可預測的順序保存物件和屬性|X|X|以可預測的順序（例如依字母順序）保存您的檔案，以促進合併。|
|重新載入|X|X|當磁片上的檔案變更時，您的編輯器必須能夠重載它。 當您參與原始檔控制時，環境會藉由呼叫您的執行來為您重載資料 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 。 最困難的重載案例是當您呼叫 IVsQueryEditQuerySave：： <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 且正在處理資訊時，簽出時發生。 不過，您的重載程式碼必須能夠在此情況下執行。<br /><br /> 環境會自動重載專案檔。 但是，如果專案有嵌套階層，則必須執行專案， <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 以支援重載嵌套的專案檔。|

## <a name="see-also"></a>另請參閱
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
