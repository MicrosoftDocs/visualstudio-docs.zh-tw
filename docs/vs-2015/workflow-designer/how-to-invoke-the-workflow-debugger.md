---
title: HOW TO：叫用工作流程偵錯工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9e607e3229225c2eeafe530ee685691b25f5ecfe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944431"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>HOW TO：叫用工作流程偵錯工具
一般而言，偵錯工作流程的方式就如同偵錯以其他 Visual Studio 程式語言撰寫的程式。 您可以利用下列方式啟動工作流程偵錯工具：  
  
-   選取  **připojit k procesu**上**偵錯**功能表來選取您的工作流程執行個體執行的主控件程序。 此程序與在 Managed 程式碼中附加至裝載程序一樣。  
  
-   按下**F5**開始執行的工作流程執行個體，或叫用中斷點後繼續執行。  
  
-   使用遠端偵錯。 如需使用遠端偵錯資訊，請參閱[How to:啟用遠端偵錯](http://go.microsoft.com/fwlink/?LinkId=196257)。  
  
    > [!NOTE]
    >  如果工作流程應用程式目標設為 x86 架構，而您的電腦執行 64 位元作業系統上裝載，則遠端偵錯將無法運作，除非[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]安裝在遠端電腦或目標工作流程應用程式變更為**任何 CPU**。  
  
### <a name="stepping-through-code"></a>逐步執行程式碼  
  
-   **中的步驟**:您可以逐步執行的活動使用**F11**。 偵錯工具會逐步執行任何已定義的處理常式。 如果沒有定義處理常式，則不進入該活動；若為包含其他活動的複合活動，則逐步執行第一個執行中活動。  
  
-   **跳離函式：** 逐步跳出活動使用**Shift-F11**。 逐步跳出活動會將目前活動及其同層級活動執行到完成。 接著偵錯工具會在目前活動的父代上中斷。 從程式碼處理常式逐步跳出時，偵錯工具會在處理常式所關聯的活動上中斷。  
  
-   **不進入函式**:您可以不進入活動使用**F10**。 跳出複合活動時，偵錯工具在複合活動的第一個可執行子系上中斷。 不進入非複合活動 (例如，<xref:System.Activities.Statements.Assign> 活動) 時，偵錯工具會執行活動及其相關聯的處理常式，並在下一個活動上中斷。 如果執行的活動是複合活動中最後一個子活動，則在執行後，偵錯工具會在父活動上中斷。  
  
### <a name="debugging-with-f5"></a>以 F5 偵錯  
  
-   如果您要建置的工作流程主控台應用程式專案，只要按下**F5**開始進行偵錯您的應用程式和工作流程。 如果您正在自行建置活動程式庫，必須使用可執行的裝載應用程式做為啟始專案。 若要在 設定啟始專案**方案總管**，以滑鼠右鍵按一下主應用程式的專案名稱，然後選取**設定為啟始專案**。  
  
## <a name="see-also"></a>另請參閱  
 [如何：在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [使用工作流程設計工具偵錯工作流程](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)