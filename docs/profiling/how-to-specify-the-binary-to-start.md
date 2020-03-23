---
title: 如何：指定要啟動的二進位檔 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fd3379b9769cfd6bfe1335b12545e635a9bde782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778683"
---
# <a name="how-to-specify-the-binary-to-start"></a>如何：指定要啟動的二進位檔

要分析二進位檔案（如 DLL），必須在**\<"目標>屬性頁"** 對話方塊中輸入資訊。 這項資訊會指示 DLL 專案可以在何處找到呼叫的應用程式。

1. 在 [效能總管]**** 中，以滑鼠右鍵按一下目標二進位檔，然後按一下 [屬性]****。

2. 在 [屬性頁]**** 對話方塊中，按一下 [啟動]**** 屬性。

3. 選取 [覆寫專案屬性]**** 核取方塊。

4. 在 [要啟動的可執行檔]**** 文字方塊中，指定檔案位置。

5. 在 [引數]**** 文字方塊中，指定啟動應用程式所需的引數。

6. 在 [工作目錄]**** 文字方塊中，指定目錄位置。

7. 按一下 [確定]****。

## <a name="see-also"></a>另請參閱

[配置性能會話](../profiling/configuring-performance-sessions.md)
