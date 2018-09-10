---
title: 錯誤： 遠端電腦不會顯示在 [遠端連線] 對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f91358597ce19f9dac1341831364dafb1fcabae
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284155"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>錯誤：遠端電腦未顯示於 [遠端連線] 對話方塊
如果遠端電腦沒有出現在 [遠端連接] 對話方塊中，請檢查下列常見的原因。  
  
 如果您使用 managed 相容性模式，請檢查 Visual Studio 2010 文件：[疑難排解遠端偵錯-Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100))。  
  
### <a name="common-causes-for-this-error"></a>這項錯誤的常見原因  
  
-   執行遠端機器的電腦位於不同的子網路中。 若要修正此問題，請在 [限定詞] 對話方塊中手動輸入電腦名稱或 IP 位址  
  
-   遠端電腦上並未執行遠端偵錯工具。 若要修正此問題，請啟動遠端偵錯工具。  
  
-   防火牆封鎖 Visual Studio 和遠端電腦之間的通訊。 若要修正此問題，請設定防火牆允許 Visual Studio 和遠端偵錯工具 (msvsmon) 進行通訊。  
  
-   防毒軟體封鎖 Visual Studio 和遠端電腦之間的通訊。 若要修正此問題，請設定防毒軟體允許 Visual Studio 和遠端偵錯工具 (msvsmon) 進行通訊。  
  
## <a name="see-also"></a>另請參閱  
 [遠端偵錯](../debugger/remote-debugging.md)