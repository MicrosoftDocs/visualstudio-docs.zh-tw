---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 26d9169be242990b9ca99b4fe4fe043d56fb7f30
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2019
ms.locfileid: "67256167"
---
您應該能夠使用您在 Visual Studio 電腦產生的符號偵錯程式碼。 當您使用本機符號時，遠端偵錯工具的效能會更好。  如果您必須使用遠端符號，就必須告訴 [遠端偵錯監視] 在遠端電腦上尋找符號。  

從 Visual Studio 2013 Update 2 開始，您可以使用下列的 msvsmon 命令列參數，以便在 Managed 程式碼中使用遠端符號：`Msvsmon /FallbackLoadRemoteManagedPdbs`  

如需詳細資訊，請參閱遠端偵錯的說明 (在 [遠端偵錯工具] 視窗中按 **F1**，或按一下 [協助] / [使用量]  )。 如需詳細資訊，請參閱 [Visual Studio 2012 和 2013 中的 .NET 遠端符號載入變更](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)
