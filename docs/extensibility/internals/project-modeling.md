---
title: 專案模型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adb0204afd889ab487070578d136aea736bb63a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130576"
---
# <a name="project-modeling"></a>專案模型
您的專案實作標準專案物件，提供自動化的下一個步驟：<xref:EnvDTE.Projects>和`ProjectItems`集合;`Project`和<xref:EnvDTE.ProjectItem>物件; 並且您的實作唯一剩餘的物件。 Dteinternal.h 檔案中，會定義這些標準的物件。 BscPrj 範例中提供的標準物件實作。 您也可以為模型使用這些類別，建立您自己獨立的並排的標準專案物件與從其他專案類型的專案物件。  
  
 自動化取用者會假設要能夠呼叫<xref:EnvDTE.Solution>(「`<UniqueProjName>")`和<xref:EnvDTE.ProjectItems>(`n`) 其中 n 是取得特定方案的專案中的索引編號。 進行此自動化呼叫導致環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A>上適當的專案階層架構，傳遞 VSITEMID_ROOT 做 VSHPROPID_ExtObject VSHPROPID 參數做為項目識別碼參數。 `IVsHierarchy::GetProperty` 傳回`IDispatch`提供核心的 automation 物件的指標`Project`您已實作的介面。  
  
 以下是語法`IVsHierarchy::GetProperty`。  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 專案容納巢狀結構，並使用集合來建立的專案項目群組。 階層看起來像這樣。  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 巢狀結構指的<xref:EnvDTE.ProjectItem>物件可以是<xref:EnvDTE.ProjectItems>同時集合因為`ProjectItems`集合可以包含巢狀的物件。 基本專案範例並未示範此巢狀結構。 藉由實作`Project`物件，您可以參與樹狀結構的整體的自動化模型設計的。  
  
 專案自動化會遵循下列圖表中的路徑。  
  
 ![Visual Studio 專案物件](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
專案自動化  
  
 如果您沒有實作`Project`物件時，環境仍會傳回泛型`Project`物件，其中包含專案的名稱。  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>