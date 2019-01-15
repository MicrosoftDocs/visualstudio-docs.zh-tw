---
title: HOW TO：重新配置所檢測的二進位檔 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8b50c5b76ea5b22bc9d734d32e433db1c7594d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893074"
---
# <a name="how-to-relocate-instrumented-binaries"></a>HOW TO：重新配置所檢測的二進位檔

在檢測期間，會將探查插入二進位檔，以便測量應用程式效能。 藉由選擇重新配置所檢測的二進位檔，可以檢測原始二進位檔的複本，並將此複本放在指定的位置。 如果您不想讓分析工具重新命名原始的二進位檔，這個選項會很有用。 如果未重新配置二進位檔，則會覆寫二進位檔的原始版本。

## <a name="to-relocate-instrumented-binary"></a>重新配置所檢測的二進位檔

1. 在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性] 。

2. 在 [屬性頁] 中，按一下 [二進位檔]  屬性。

3. 選取 [重新配置所檢測的二進位檔]  核取方塊。

4. 指定所檢測之二進位檔的位置。

## <a name="see-also"></a>另請參閱

[設定效能工作階段](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
