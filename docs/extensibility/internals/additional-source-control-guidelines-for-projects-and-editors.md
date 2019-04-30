---
title: 專案和編輯器適用的其他原始檔控制指導方針 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3566709819d2023dfd6e38e40f88a454de83e3e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861735"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>專案和編輯器適用的其他原始檔控制指導方針
有幾個的專案和編輯器應符合以支援原始檔控制的指導方針。

## <a name="guidelines"></a>方針
 您的專案或編輯器應該也會執行以下動作來支援原始檔控制：

|區域|專案|編輯器|詳細資料|
|----------|-------------|------------|-------------|
|私用檔案的複本|X||環境支援檔案的私用的複本。 也就是登錄在專案中每個人都他/她自己的私用複本，該專案中的檔案。|
|ANSI/Unicode 持續性|X|X|如果您撰寫持續性程式碼時，保存 ANSI 格式的檔案，因為大部分的原始檔控制程式目前不支援 Unicode。|
|列舉的檔案|X||專案必須包含特定的清單中的所有檔案，而且必須能夠列舉檔案的清單<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling)。 專案應該也會公開項目名稱，透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>的實作和支援名稱查閱 （包括特殊的檔案） 透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>實作。|
|文字格式|X|X|如果可能的話，檔案應為以文字格式，以支援不同版本的合併。 無法與其他版本的檔案稍後合併並不是文字格式的檔案。 慣用的文字格式為 XML。|
|參考架構|X||原始檔控制中輕易地支援參考為基礎的專案。 不過，目錄為基礎的專案也支援原始檔控制，只要專案可能會產生一份其隨，不論這些檔案是否存在於磁碟上的檔案。 當從原始檔控制中開啟專案，會將專案檔關機之前的任何其檔案的第一個。|
|保存中預期的順序物件和屬性|X|X|保存您的檔案，可預測的順序，例如依字母順序排列的順序，以利於進行合併。|
|重新載入|X|X|檔案變更時在磁碟上，您的編輯器必須能夠重新載入它。 當您參與原始檔控制時，環境將會重新載入資料，藉由呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實作。 您有呼叫 IVsQueryEditQuerySave 時，就會發生簽出時，最困難的重新載入案例::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和處理資訊。 不過，您的重新載入程式碼必須能夠在此情況下執行。<br /><br /> 環境會自動重新載入專案檔。 不過，專案必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>如果它有巢狀階層，才能支援重新載入巢狀專案檔案。|

## <a name="see-also"></a>另請參閱
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)