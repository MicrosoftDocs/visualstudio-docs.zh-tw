---
title: 如何：還原隱藏的偵錯工具命令 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 297be3a3a4ad3c70ad28c627d5dc8d64c6ba1c7a
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147235"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>如何：還原隱藏的偵錯工具命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您設定 Visual Studio 時，將會要求您選擇一組預設 IDE 設定，做為您主要的程式設計語言。 某些語言的預設 IDE 設定可能會隱藏特定偵錯工具命令。  
  
 如果想要使用預設 IDE 設定所隱藏的偵錯工具功能，您可以執行下列程序，將命令加回功能表中。  
  
### <a name="to-restore-hidden-debugger-commands"></a>若要還原隱藏的偵錯工具命令  
  
1. 當專案開啟時，在 [工具]**** 功能表上，按一下 [自訂]****。  
  
2. 在 [自訂]  對話方塊中，按一下 [命令]  索引標籤。  
  
3. 在 [功能表列:]**** 下拉式清單中，選取要包含所還原命令的 [偵錯]**** 功能表。  
  
4. 按一下 [ **新增] 命令 ...** 按鈕。  
  
5. 在 [加入命令]**** 方塊中，選取您要加入的命令，然後按一下 [確定]****。  
  
6. 重複以上步驟來加入其他命令。  
  
7. 將想要的命令加入功能表之後，按一下 [關閉]****。  
  
    > [!WARNING]
    > 有些功能表項目只會在偵錯工具處於特定模式時出現，例如，執行模式或中斷模式。 因此，當您完成以上步驟時，可能不會立即看見您所加入的項目。  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>從自訂對話方塊還原無法使用的命令  
 有些命令可能無法從 [自訂]**** 對話方塊還原，特別是出現在階層式功能表中的命令。 若要還原這些命令，您必須匯入新的 IDE 設定集合。  
  
#### <a name="to-import-new-ide-settings"></a>若要匯入新的 IDE 設定  
  
1. 按一下 [工具]**** 功能表上的 [匯入和匯出設定]****。  
  
2. 在 [歡迎使用匯入和匯出設定精靈]**** 頁面上，按一下 [匯入選取的環境設定]****，再按 [下一步]****。  
  
3. 在 [儲存目前的設定值]**** 頁面上，選擇是否要儲存現有的設定值，再按 [下一步]****。  
  
4. 在 [選擇要匯入的設定集合]**** 頁面的 [預設值]**** 資料夾底下，選擇含有您想要使用之命令的開發設定集合。 如果不知道應該選擇那個集合，請嘗試 [一般開發設定]**** 或 [Visual C++ 開發設定]****，這兩個提供了大部分的偵錯工具命令。  
  
5. 按 [下一步]  。  
  
6. 在 [選擇要匯入的設定]**** 頁面的 [選項]**** 底下，確定已經選取 [偵錯]****。 若不要再匯入其他設定，請清除那些核取方塊。  
  
7. 按一下 [完成] 。  
  
8. 在 [匯入完成]**** 頁面上，檢閱任何在 [詳細資料]**** 下與重設設定關聯的任何錯誤。  
  
9. 按一下 [關閉] 。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具安全性](../debugger/debugger-security.md)   
 [偵錯工具基礎](../debugger/debugger-basics.md)
