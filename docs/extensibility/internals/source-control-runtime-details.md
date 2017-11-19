---
title: "原始檔控制執行階段詳細資料 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9647f1f399b0d6516fe6475e6245c6834a0ea2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-runtime-details"></a>原始檔控制執行階段詳細資料
專案加入至原始檔控制中，當使用者將檔案加入專案中加入原始檔控制，或透過 automation 控制器，如精靈。 專案未指定本身是在原始檔控制。它支援原始檔控制，但必須手動新增它。  
  
## <a name="registering-with-a-source-control-package"></a>登錄至原始檔控制封裝  
 當您的專案中的檔案加入原始檔控制中時，環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>為您提供四種不透明的字串，可用做為 cookie 的原始檔控制系統。 這些字串儲存在專案檔。 這些字串應該傳遞至原始檔控制虛設常式 （管理原始檔控制套件的 Visual Studio 元件） 在啟動時的專案類型呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>。 這又會載入適當的原始檔控制封裝和轉送它的實作呼叫`IVsSccManager2::RegisterSccProject`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)