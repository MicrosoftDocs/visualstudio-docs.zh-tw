---
title: 如何： 清除復原堆疊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7f094723ec74bbcfe7723ea8141a6980a1465fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734686"
---
# <a name="how-to-clear-the-undo-stack"></a>如何： 清除復原堆疊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

下列程序說明如何清除復原堆疊。  
  
### <a name="to-clear-the-undo-stack"></a>若要清除復原堆疊  
  
1.  若要清除復原堆疊使用[IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799)方法。 這個範例如下：  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [如何：實作復原管理](../extensibility/how-to-implement-undo-management.md)

