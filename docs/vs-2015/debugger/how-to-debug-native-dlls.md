---
title: HOW TO：偵錯原生 Dll |Microsoft Docs
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
ms.openlocfilehash: ffc4f0b58bacdc71439a89dce711575a103c71cf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940082"
---
# <a name="how-to-debug-native-dlls"></a>HOW TO：偵錯原生 Dll
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
 當您要偵錯一個 DLL 時，您可以從下列地方開始偵錯：  
  
- 從建立會呼叫該 DLL 的可執行檔的專案。  
  
  \-或-  
  
- 從建立該 DLL 本身的專案。  
  
  如果您是使用某專案來建立可執行檔，請從該專案開始偵錯。 您可以接著開啟該 DLL 的原始程式檔 (Source File)，並在該檔案中設定中斷點，即使這個檔案並不是屬於用來建立可執行檔的專案。 如需詳細資訊，請參閱[中斷點](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
  如果您要從建立該 DLL 的專案開始偵錯，就必須指定您希望用來偵錯該 DLL 的可執行檔。  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>若要指定偵錯工作階段的可執行檔  
  
1. 在 [**方案總管] 中**，選取建立該 DLL 的專案。  
  
2. 從**檢視**功能表上，選擇**屬性頁**。  
  
3. 在 **屬性頁**對話方塊中，開啟**組態屬性**資料夾，然後選取**偵錯**類別目錄。  
  
4. 在 **命令**方塊中，指定容器的路徑名稱。 例如 C:\Program Files\MyApplication\MYAPP.EXE。  
  
5. 在 **命令列引數**方塊中，指定任何必要的引數，可執行檔。  
  
   如果您未指定之可執行檔_專案_**屬性頁** 對話方塊中，[可執行檔進行偵錯工作階段對話方塊](../debugger/executable-for-debugging-session-dialog-box.md)啟動偵錯時出現。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)
