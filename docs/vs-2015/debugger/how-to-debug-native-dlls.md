---
title: 如何：調試原生 Dll |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702672"
---
# <a name="how-to-debug-native-dlls"></a>如何：偵錯原生 DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 當您要偵錯一個 DLL 時，您可以從下列地方開始偵錯：  
  
- 從建立會呼叫該 DLL 的可執行檔的專案。  
  
  \- 或 -  
  
- 從建立該 DLL 本身的專案。  
  
  如果您是使用某專案來建立可執行檔，請從該專案開始偵錯。 您可以接著開啟該 DLL 的原始程式檔 (Source File)，並在該檔案中設定中斷點，即使這個檔案並不是屬於用來建立可執行檔的專案。 如需詳細資訊，請參閱[中斷點](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
  如果您要從建立該 DLL 的專案開始偵錯，就必須指定您希望用來偵錯該 DLL 的可執行檔。  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>若要指定偵錯工作階段的可執行檔  
  
1. 在 **方案總管**中，選取建立 DLL 的專案。  
  
2. 從 [ **View** ] 功能表選擇 [**屬性頁**]。  
  
3. 在 [ **屬性頁** ] 對話方塊中，開啟 [設定 **屬性** ] 資料夾，然後選取 [ **調試** 類別目錄]。  
  
4. 在 [ **命令** ] 方塊中，指定容器的路徑名稱。 例如 C:\Program Files\MyApplication\MYAPP.EXE。  
  
5. 在 [ **命令引數** ] 方塊中，指定可執行檔的任何必要引數。  
  
   如果您未在 [ _專案_**屬性頁** ] 對話方塊中指定可執行檔，則當您開始進行偵錯工具時，會出現 [ [可執行檔的偵錯工具] 對話方塊](../debugger/executable-for-debugging-session-dialog-box.md) 。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)
