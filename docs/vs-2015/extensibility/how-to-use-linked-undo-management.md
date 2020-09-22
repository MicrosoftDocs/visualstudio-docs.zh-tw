---
title: 如何：使用連結的復原管理 |Microsoft Docs
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
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838889"
---
# <a name="how-to-use-linked-undo-management"></a>如何：使用連結的復原管理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

連結的復原可讓使用者同時在多個檔案中復原相同的編輯。 例如，在多個程式檔中的同步文字變更，例如標頭檔和 Visual C++ 檔案，都是連結的復原交易。 連結的復原功能內建在環境的復原管理員中， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> 可讓您操作這項功能。 連結的復原是由父系復原單位所執行，此單元可將個別的復原堆疊連結在一起，以視為單一復原單位。 下一節將詳細說明使用連結復原的程式。  
  
### <a name="to-use-linked-undo"></a>使用連結的復原  
  
1. 呼叫 `QueryService` `SVsLinkedUndoManager` 以取得的指標 `IVsLinkedUndoTransactionManager` 。  
  
2. 藉由呼叫來建立初始父連結的復原單位 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> 。 這會設定一組復原堆疊的起點，以組成連結的復原堆疊。 在 `OpenLinkedUndo` 方法中，您也需要指定是否要讓連結的復原成為 strict 或非嚴格的。 非嚴格連結的復原行為表示具有連結的恢復同級的部分檔可以關閉，並且仍將其他連結的復原同級保留在堆疊上。 嚴格連結的復原行為會指定所有連結的恢復同級都必須同時復原或完全不使用。 藉由呼叫 [IOleUndoManager：： add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) 方法，新增後續連結的復原堆疊。  
  
3. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> 以將所有連結的恢復單元復原成一個。  
  
    > [!NOTE]
    > 若要在編輯器中執行連結的復原管理，請新增復原管理。 如需有關如何執行連結復原管理的詳細資訊，請參閱 [如何：執行復原管理](../extensibility/how-to-implement-undo-management.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [如何：實作復原管理](../extensibility/how-to-implement-undo-management.md)
