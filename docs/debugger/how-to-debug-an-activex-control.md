---
title: 對 ActiveX 控制項進行 Debug |Microsoft Docs
Description: 瞭解如何對 ActiveX 控制項進行調試。 您必須指定包含可執行檔，您可以在專案屬性頁中執行此動作，或在開始進行偵錯工具時執行此動作。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83522eb13350d86ef0531d90b3db844ece8f6655
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913414"
---
# <a name="how-to-debug-an-activex-control"></a>如何：偵錯 ActiveX 控制項

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

若要偵錯您的 ActiveX 控制項，您必須指定容器 (可執行檔)，讓控制項在其中執行。

## <a name="to-specify-a-container-for-the-debug-session"></a>若要指定此偵錯工作階段的容器

1. 在 [方案總管] 中選取專案。

2. 從 [ **View** ] 功能表選擇 [ **屬性頁**]。

3. 在 [專案屬性頁] 對話方塊中，開啟 [組態屬性] 資料夾，並選取 [偵錯]。

4. 在 [偵錯] 類別下方，找出 [命令] 屬性。

5. 指定該容器的路徑名稱。 例如，C:\Program Files\Internet Explorer\IEXPLORE.EXE。

6. 如果您指定 Internet Explorer 作為容器，而且您正使用 Active Desktop，請在 [命令引數] 方塊中鍵入 `/new`。

7. 按一下 [確定]  。

     若您未在 [專案屬性頁] 對話方塊中指定容器，您也可以在開始偵錯時指定容器。 當您選取執行命令以開始偵錯時，將會出現[偵錯工作階段的可執行檔對話方塊](../debugger/executable-for-debugging-session-dialog-box.md)。 在對話方塊中指定容器的路徑名稱。

## <a name="see-also"></a>另請參閱

- [ActiveX 控制項](/cpp/mfc/activex-controls)
- [使用測試容器測試屬性和事件](/cpp/mfc/testing-properties-and-events-with-test-container)
- [COM 和 ActiveX 調試](../debugger/com-and-activex-debugging.md)
- [Visual Studio 偵錯](../debugger/index.yml)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)