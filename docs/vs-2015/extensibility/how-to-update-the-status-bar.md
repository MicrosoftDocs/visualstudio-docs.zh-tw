---
title: 如何：更新狀態列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703151"
---
# <a name="how-to-update-the-status-bar"></a>如何：更新狀態列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**狀態列**是位於許多應用程式視窗底部的控制列，其中包含一個或多個狀態文字行或指標。  
  
### <a name="to-update-the-status-bar"></a>更新狀態列  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>在每個個別的 view 物件上執行， (您編輯器提供的 DocView) ，例如表單檢視和程式碼視圖。  
  
2. 當 IDE 呼叫時 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> ，請呼叫的方法，以更新 **狀態列** 中的資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 。  
  
    > [!NOTE]
    > <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>只有在您的文件視窗一開始啟動時，IDE 才會呼叫。 如果您的文件視窗處於作用中的其餘部分，您必須在編輯器的狀態變更時更新 **狀態列** 資訊。  
  
## <a name="robust-programming"></a>穩固程式設計  
 **狀態列**包含四個不同的欄位：  
  
- 狀態文字  
  
- 進度列  
  
- 動畫圖標  
  
- 編輯器資訊  
  
  如需詳細資訊，請參閱 [狀態列](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)。  
  
  <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 當您的文件視窗啟用時，IDE 會自動呼叫您的執行方法。  
  
  VSPackage 實施者負責更新狀態列中的狀態文字。 如果狀態文字欄位設定為空白文字 ( "" ) 處於閒置時間，則 IDE 會將這個字串重設為「就緒」。  
  
## <a name="see-also"></a>另請參閱  
 [狀態列](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
