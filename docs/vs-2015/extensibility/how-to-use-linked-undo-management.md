---
title: HOW TO：使用連結的復原管理 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 442024b7be335c0aa010ce528142ac7a205097f8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062967"
---
# <a name="how-to-use-linked-undo-management"></a>HOW TO：使用連結的復原管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

連結的復原可讓使用者同時復原所做的相同編輯多個檔案中。 例如，跨多個程式檔，例如標頭檔和視覺效果的同時文字變更C++檔案中，連結的復原交易。 連結的復原功能內建於復原管理員 中，環境的實作和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>可讓您管理這項功能。 連結的復原會實作可以連結在一起，以視為單一復原單元的個別復原堆疊為父系復原單位。 使用連結的復原的程序會在下一節中詳細說明。  
  
### <a name="to-use-linked-undo"></a>若要使用連結的復原  
  
1. 呼叫`QueryService`上`SVsLinkedUndoManager`若要取得的指標`IVsLinkedUndoTransactionManager`。  
  
2. 藉由呼叫建立初始的父連結的復原單位<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>。 這會設定一組復原堆疊來分組為連結的復原堆疊的起點。 在 `OpenLinkedUndo`您也必須指定您要連結的復原，為 strict 或非嚴格的方法。 非嚴格連結的復原行為表示某些連結的復原同層級的文件可以關閉，且仍保留其他連結復原其在堆疊上的同層級。 Strict 連結的復原行為會指定所有連結的復原同層級堆疊必須一起或完全不會復原。 新增後續的連結藉由呼叫復原堆疊[IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add)方法。  
  
3. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>以向前復原所有做為其中一個連結的復原單位。  
  
    > [!NOTE]
    >  若要實作連結的復原管理在編輯器中，將復原管理。 如需有關如何實作連結的復原管理的詳細資訊，請參閱[How to:實作復原管理](../extensibility/how-to-implement-undo-management.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [如何：實作復原管理](../extensibility/how-to-implement-undo-management.md)
