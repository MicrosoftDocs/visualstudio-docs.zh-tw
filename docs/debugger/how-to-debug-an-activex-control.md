---
title: HOW TO：Debug an ActiveX Control |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 059dde50a01c1c71545a187043e60a32a9e68309
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269679"
---
# <a name="how-to-debug-an-activex-control"></a>HOW TO：對 ActiveX 控制項進行偵錯

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

若要偵錯您的 ActiveX 控制項，您必須指定容器 (可執行檔)，讓控制項在其中執行。

## <a name="to-specify-a-container-for-the-debug-session"></a>若要指定此偵錯工作階段的容器

1.  在 [方案總管] 中選取專案。

2.  從**檢視**功能表上，選擇**屬性頁**。

3.  在 [專案屬性頁] 對話方塊中，開啟 [組態屬性] 資料夾，並選取 [偵錯]。

4.  在 [偵錯] 類別下方，找出 [命令] 屬性。

5.  指定該容器的路徑名稱。 例如，C:\Program Files\Internet Explorer\IEXPLORE.EXE。

6.  如果您指定 Internet Explorer 作為容器，而且您正使用 Active Desktop，請在 [命令引數] 方塊中鍵入 `/new`。

7.  按一下 [確定 **Deploying Office Solutions**]。

     若您未在 [專案屬性頁] 對話方塊中指定容器，您也可以在開始偵錯時指定容器。 當您選取執行命令以開始偵錯時，將會出現[偵錯工作階段的可執行檔對話方塊](../debugger/executable-for-debugging-session-dialog-box.md)。 在對話方塊中指定容器的路徑名稱。

## <a name="see-also"></a>請參閱

- [ActiveX 控制項](/cpp/mfc/activex-controls)
- [使用測試容器測試屬性和事件](/cpp/mfc/testing-properties-and-events-with-test-container)
- [偵錯 COM 和 ActiveX](../debugger/com-and-activex-debugging.md)
- [Visual Studio 偵錯](../debugger/index.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)