---
title: 指定檢測前置和檢測後續命令 | Microsoft Docs
description: 瞭解如何在檢測效能會話中的二進位檔之前或之後，指定要執行的命令。
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7f5bc12a8b0ffb7ef0fa1a78b771ced829f4d73c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955810"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>如何：指定檢測前置和檢測後續命令

您可以指定要在檢測效能工作階段中的二進位檔之前或之後執行的命令。 任何可從命令列發出的命令都可以指定為檢測前置或檢測後續事件。 例如，您可以在檢測二進位檔之後執行的批次檔中，指定使用強式名稱金鑰自動重新簽署組件的命令。

您可以針對程式碼剖析執行中所有已檢測的二進位檔或針對個別二進位檔指定命令。 不過，您只能指定一個要在檢測程序之前執行的檢測前置命令，以及一個要在之後執行的檢測後續命令。 但無法同時針對所有二進位檔及個別二進位檔指定命令。 針對所有二進位檔指定命令時，會在檢測工作階段中的每個二進位檔之前或之後執行命令。

執行命令的工作目錄取決於您執行 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 的作業系統以及已進行分析之應用程式的目標平台。

若要取得分析工具的路徑，請參閱[指定命令列工具的路徑](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)。

## <a name="to-specify-pre-instrument-commands"></a>指定檢測前置命令

1. 請執行下列其中一個步驟：

    - 若要針對效能工作階段中的所有二進位檔指定檢測前置命令，請在 [效能總管] 中選取效能工作階段節點，然後按一下滑鼠右鍵並選取 [屬性]。

    - 若要針對特定二進位檔指定檢測前置命令，請在效能工作階段的 [目標] 清單中，以滑鼠右鍵按一下二進位檔的名稱，然後選取 [屬性]。

2. 在 [屬性頁] 中，按一下 [檢測]。

3. 在 [檢測前置事件] 底下的 [命令列] 文字方塊中輸入命令。

    > [!NOTE]
    > 您可以按一下 [**命令列**] 方塊旁邊的省略號按鈕 **( ... )** ，以流覽並選取適當的 .exe、.cmd 或 .bat 檔案。

4. 按一下 [確定]  。

     若要停止執行命令但不將它移除，請選取 [從檢測中排除] 核取方塊。 若要修改編譯器或連結器設定，請使用專案屬性頁。

## <a name="to-specify-post-instrument-commands"></a>指定檢測後續命令

1. 請執行下列其中一個步驟：

    - 若要針對效能工作階段中的所有二進位檔指定檢測後續命令，請在 [效能總管] 中選取效能工作階段節點，然後按一下滑鼠右鍵並選取 [屬性]。

    - 若要針對特定二進位檔指定檢測後續命令，請在效能工作階段的 [目標] 清單中，以滑鼠右鍵按一下二進位檔的名稱，然後選取 [屬性]。

2. 在 [屬性頁] 中，按一下 [檢測]。

3. 在 [檢測後續事件] 底下的 [命令列] 文字方塊中輸入命令。

    > [!NOTE]
    > 您可以按一下 [**命令列**] 方塊旁邊的省略號按鈕 **( ... )** ，以流覽並選取適當的 .exe、.cmd 或 .bat 檔案。

4. 按一下 [確定]  。

     若要停止執行命令但不將它移除，請選取 [從檢測中排除] 核取方塊。 若要修改編譯器或連結器設定，請使用專案屬性頁。

## <a name="see-also"></a>另請參閱

[設定效能工作階段](../profiling/configuring-performance-sessions.md)
