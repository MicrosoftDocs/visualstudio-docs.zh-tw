---
title: 警告：已停用腳本調試 |Microsoft Docs
description: 當您嘗試在不啟用腳本的 Internet Explorer 中啟用腳本時，就會發生「停用腳本偵測」警告。 請參閱啟用的步驟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cc2e03a4efcf9a88675fd3c80f374ff78ba35bb
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149556"
---
# <a name="warning-script-debugging-disabled"></a>警告：已停用指令碼偵錯
在 Internet Explorer 中，目前停用指令碼偵錯功能

 當您在 Internet Explorer 中嘗試對指令檔進行偵錯，卻沒有啟用 Internet Explorer 的指令檔偵錯功能，這個警告就會出現。 基於安全性考量，在 Internet Explorer 中預設是停用指令碼偵錯功能。

### <a name="to-enable-script-debugging-in-internet-explorer"></a>若要在 Internet Explorer 中啟用指令碼偵錯

1. 在 Internet Explorer 中，從 [工具] 功能表選擇 [網際網路選項]。

2. 在 [網際網路選項] 對話方塊中，按一下 [進階] 索引標籤。

3. 在 [進階] 索引標籤中，查看 [設定] 方塊下的 [瀏覽] 分類。

4. 清除 [停用指令碼偵錯 (Internet Explorer)]。

5. 按一下 [確定]。

6. 結束並且重新啟動 Internet Explorer。

     新的設定目前已經生效。

## <a name="see-also"></a>另請參閱
- [如何：附加至腳本](attach-to-running-processes-with-the-visual-studio-debugger.md)