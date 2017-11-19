---
title: "如何： 使用管理的已連結的復原 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05e10305f7e4c243f799cfe33d4d9b86418eed86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-linked-undo-management"></a>如何： 使用已連結的復原管理
已連結的復原可讓使用者同時復原多個檔案中相同的編輯。 比方說，跨多個程式檔，例如標頭檔和 Visual c + + 檔案，同時文字變更為已連結的復原交易。 連結的復原功能已內建復原管理員 中，環境的實作和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>可讓您管理這項功能。 可以連結在一起，以被視為單一復原單位個別復原堆疊父復原單位來執行的已連結的復原。 下一節會詳細說明使用的已連結的復原的程序。  
  
### <a name="to-use-linked-undo"></a>若要使用的已連結的復原  
  
1.  呼叫`QueryService`上`SVsLinkedUndoManager`取得指標`IVsLinkedUndoTransactionManager`。  
  
2.  藉由呼叫建立初始父連結的復原單位<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>。 這會設定復原堆疊來分組的已連結的復原堆疊為一組的開始點。 在`OpenLinkedUndo`方法，您也必須指定您是否要嚴格或非嚴格的已連結的復原。 非嚴格的已連結的復原行為表示某些已連結的復原同層級的文件可以關閉，而且仍保留其他連結復原其在堆疊上的同層級。 嚴格的已連結的復原行為會指定所有的已連結的復原同層級堆疊必須一起或完全不能復原。 新增連結後續復原堆疊藉由呼叫[IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135)方法。  
  
3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>向前復原所有的其中一個連結的復原單位。  
  
    > [!NOTE]
    >  若要實作的已連結的復原管理在編輯器中，新增復原管理。 如需實作的已連結的復原管理的詳細資訊，請參閱[How to： 實作復原管理](../extensibility/how-to-implement-undo-management.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [如何： 實作復原管理](../extensibility/how-to-implement-undo-management.md)