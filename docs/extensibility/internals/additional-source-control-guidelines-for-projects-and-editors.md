---
title: "其他原始檔控制專案和方針編輯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 308de182e604f06fff9ad25cb65428b2d48ff257
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>其他原始檔控制專案和方針編輯器
有許多的專案和編輯器應該遵守才能支援原始檔控制的指導方針。  
  
## <a name="guidelines"></a>方針  
 您的專案或編輯器類型也會執行以下動作來支援原始檔控制：  
  
|區域圖|專案|編輯器|詳細資料|  
|----------|-------------|------------|-------------|  
|私用檔案的複本|X||環境可支援檔案的私用複本。 也就是加入在專案中的每一個人有其自己的私用複本，該專案中的檔案。|  
|ANSI/Unicode 持續性|X|X|如果您撰寫的持續性程式碼時，保存 ANSI 格式的檔案，因為大部分的原始檔控制程式目前不支援 Unicode。|  
|列舉的檔案|X||專案必須包含的所有檔案內的特定清單，且必須能夠使用的檔案清單的列舉<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling)。 專案應該也會公開項目名稱，透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>實作和支援的名稱查閱 （包括特殊的檔案） 透過其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>實作。|  
|文字格式|X|X|如果可能的話，檔案應該以文字格式，以支援不同版本合併。 無法與其他版本的檔案稍後合併並不是文字格式的檔案。 慣用的文字格式為 XML。|  
|參考為基礎|X||原始檔控制中輕易地支援參考為基礎的專案。 不過，目錄為基礎的專案也會受到原始檔控制，只要專案可能會產生一份其視，不論這些檔案是否存在於磁碟上的檔案。 從原始檔控制開啟專案，專案檔是關閉任何檔案之前，先的第一個。|  
|可預測的順序保存物件和屬性|X|X|保存您的可預測的順序，例如依字母順序排列的順序，以便合併檔案。|  
|重新載入|X|X|當磁碟上的檔案變更時，您的編輯器必須能夠重新載入它。 當您參與原始檔控制中時，環境會重新載入資料，藉由呼叫您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>實作。 您已呼叫 IVsQueryEditQuerySave 時發生簽出時，最困難的重新載入案例::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>和處理資訊。 不過，您重新載入的程式碼必須能夠在此情況下執行。<br /><br /> 環境會自動重新載入專案檔。 不過，專案必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>如果有巢狀階層，才能支援重新載入巢狀專案檔案。|  
  
## <a name="see-also"></a>請參閱  
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)