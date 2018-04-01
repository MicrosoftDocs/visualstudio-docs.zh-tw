---
title: 如何： 清除復原堆疊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e2592ad8bbec0ddf87731d25f5c46c714a3336d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-the-undo-stack"></a>如何： 清除復原堆疊
下列的下列程序說明如何清除復原堆疊。  
  
### <a name="to-clear-the-undo-stack"></a>若要清除復原堆疊  
  
1.  若要清除復原堆疊使用[IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799)方法。 此動作的範例如下：  
  
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
  
## <a name="see-also"></a>請參閱  
 [如何： 實作復原管理](../extensibility/how-to-implement-undo-management.md)