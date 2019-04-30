---
title: 原始檔控制執行階段詳細資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f7501a25596fc0a818277d164337bb0d4e4e077
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62858638"
---
# <a name="source-control-runtime-details"></a>原始檔控制的執行階段詳細資料
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當使用者將檔案加入專案中加入原始檔控制，或透過自動化控制站，例如精靈時，專案會加入原始檔控制。 專案未指定為其本身，是在原始檔控制它支援原始檔控制，但必須以手動方式新增至它。  
  
## <a name="registering-with-a-source-control-package"></a>使用原始檔控制套件註冊  
 當您的專案中的檔案新增至原始檔控制時，環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>為您提供四個為 cookie 由原始檔控制系統的不透明字串。 將這些字串儲存在您的專案檔中。 這些字串應該傳遞至原始檔控制虛設常式 （管理原始檔控制套件的 Visual Studio 元件） 在啟動時的專案類型呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>。 這接著會載入適當的原始檔控制封裝，並會轉送它的實作呼叫`IVsSccManager2::RegisterSccProject`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
