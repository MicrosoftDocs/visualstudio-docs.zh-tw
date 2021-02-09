---
title: 遠端電腦未出現在 [遠端連線] 對話方塊中 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be39d733b2e5fe83fa9f7e2241c7de06980bb583
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871361"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>錯誤：遠端電腦未顯示於 [遠端連線] 對話方塊
如果遠端電腦沒有出現在 [遠端連接] 對話方塊中，請檢查下列常見的原因。

 如果您使用受控相容性模式，請參閱 Visual Studio 2010 文件：[Troubleshooting Remote Debugging - Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)) (疑難排解遠端偵錯 - Visual Studio 2010)。

### <a name="common-causes-for-this-error"></a>這項錯誤的常見原因

- 執行遠端機器的電腦位於不同的子網路中。 若要修正此問題，請在 [限定詞] 對話方塊中手動輸入電腦名稱或 IP 位址

- 遠端電腦上並未執行遠端偵錯工具。 若要修正此問題，請啟動遠端偵錯工具。

- 防火牆封鎖 Visual Studio 和遠端電腦之間的通訊。 若要修正此問題，請設定防火牆允許 Visual Studio 和遠端偵錯工具 (msvsmon) 進行通訊。

- 防毒軟體封鎖 Visual Studio 和遠端電腦之間的通訊。 若要修正此問題，請設定防毒軟體允許 Visual Studio 和遠端偵錯工具 (msvsmon) 進行通訊。

## <a name="see-also"></a>另請參閱
- [遠端偵錯](../debugger/remote-debugging.md)