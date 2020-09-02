---
title: 執行單一檔案產生器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192698"
---
# <a name="implementing-single-file-generators"></a>實作單一檔案產生器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

自訂工具（有時稱為單一檔案產生器）可用來擴充 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 和 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 中的專案系統 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 自訂工具是可實介面的 COM 元件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 。 使用這個介面時，自訂工具會將單一輸入檔轉換成單一輸出檔。 轉換的結果可能是原始程式碼，或任何其他有用的輸出。 自訂工具產生的程式碼檔案有兩個範例，是為了回應視覺化設計工具中的變更而產生的程式碼，以及使用 Web 服務描述語言 (WSDL) 產生的檔案。  
  
 載入自訂工具或儲存輸入檔時，專案系統會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 方法，並傳遞 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 回呼介面的參考，讓此工具可以向使用者報告其進度。  
  
 自訂工具產生的輸出檔會加入至具有輸入檔相依性的專案。 專案系統會根據自訂工具的執行所傳回的字串，自動決定輸出檔的名稱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> 。  
  
 自訂工具必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 介面。 （選擇性）自訂工具支援 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 介面，以從輸入檔以外的來源取得資訊。 在任何情況下，您必須先向系統或在本機登錄中註冊，才能使用自訂工具 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。 如需註冊自訂工具的詳細資訊，請參閱 [註冊單一](../../extensibility/internals/registering-single-file-generators.md)檔案產生器。  
  
## <a name="see-also"></a>另請參閱  
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)   
 [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)
