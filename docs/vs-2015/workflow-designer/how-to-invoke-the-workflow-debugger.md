---
title: 如何：叫用工作流程偵錯工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292887"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>HOW TO：叫用工作流程偵錯工具
一般而言，偵錯工作流程的方式就如同偵錯以其他 Visual Studio 程式語言撰寫的程式。 您可以利用下列方式啟動工作流程偵錯工具：

- 選取 [**偵錯**] 功能表上的 [**附加至處理序**]，選取工作流程執行個體的執行中裝載程序。 此程序與在 Managed 程式碼中附加至裝載程序一樣。

- 按下 **F5** 以開始執行工作流程的執行個體，或在叫用中斷點後繼續執行。

- 使用遠端偵錯。 如需使用遠端偵錯程式的詳細資訊，請參閱[如何：啟用遠端偵錯](https://go.microsoft.com/fwlink/?LinkId=196257)。

    > [!NOTE]
    > 如果工作流程應用程式的目標為 x86 架構，並裝載在執行 64 位元作業系統的機器上，則遠端偵錯將不會運作，除非 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 安裝在遠端機器上，或工作流程應用程式的目標變更為 [**任何 CPU**]。

### <a name="stepping-through-code"></a>逐步執行程式碼

- **逐步執行**：使用 [**F11**] 逐步進入活動。 偵錯工具會逐步執行任何已定義的處理常式。 如果沒有定義處理常式，則不進入該活動；若為包含其他活動的複合活動，則逐步執行第一個執行中活動。

- **跳離函式**：使用 **Shift-F11** 逐步跳出活動。 逐步跳出活動會將目前活動及其同層級活動執行到完成。 接著偵錯工具會在目前活動的父代上中斷。 從程式碼處理常式逐步跳出時，偵錯工具會在處理常式所關聯的活動上中斷。

- **不進入函式**：使用 **F10** 不進入活動。 跳出複合活動時，偵錯工具在複合活動的第一個可執行子系上中斷。 不進入非複合活動 (例如，<xref:System.Activities.Statements.Assign> 活動) 時，偵錯工具會執行活動及其相關聯的處理常式，並在下一個活動上中斷。 如果執行的活動是複合活動中最後一個子活動，則在執行後，偵錯工具會在父活動上中斷。

### <a name="debugging-with-f5"></a>以 F5 偵錯

- 如果您正在建置工作流程主控台應用程式專案，只要按下 **F5** 即可開始在應用程式與工作流程中偵錯。 如果您正在自行建置活動程式庫，必須使用可執行的裝載應用程式做為啟始專案。 若要在 [**方案總管**] 中設定啟始專案，請以滑鼠右鍵按一下裝載的專案名稱，並選取 [**設定為啟始專案**]。

## <a name="see-also"></a>另請參閱
 [如何：在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)[使用工作流程設計工具的調試工作流程](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)