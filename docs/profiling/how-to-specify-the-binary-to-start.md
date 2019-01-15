---
title: HOW TO：指定要啟動的二進位檔 | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c569b9e285e4865b8ef637443acdf6026b0fec9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868465"
---
# <a name="how-to-specify-the-binary-to-start"></a>HOW TO：指定要啟動的二進位檔

若要剖析二進位檔 (如 DLL)，您必須在 [\<目標> 屬性頁] 對話方塊中輸入資訊。 這項資訊會指示 DLL 專案可以在何處找到呼叫的應用程式。

1. 在 [效能總管] 中，以滑鼠右鍵按一下目標二進位檔，然後按一下 [屬性]。

2. 在 [屬性頁] 對話方塊中，按一下 [啟動] 屬性。

3. 選取 [覆寫專案屬性] 核取方塊。

4. 在 [要啟動的可執行檔] 文字方塊中，指定檔案位置。

5. 在 [引數] 文字方塊中，指定啟動應用程式所需的引數。

6. 在 [工作目錄] 文字方塊中，指定目錄位置。

7. 按一下 [確定 **Deploying Office Solutions**]。

## <a name="see-also"></a>另請參閱

[設定效能工作階段](../profiling/configuring-performance-sessions.md)