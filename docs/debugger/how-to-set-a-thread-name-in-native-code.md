---
title: HOW TO：在機器碼中設定執行緒名稱 |Microsoft Docs
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d37a028fb5af099484d81374e52cfd12af727f94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847534"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>HOW TO：在機器碼中設定執行緒名稱
在所有 Visual Studio 版本中，都可以將執行緒命名。 執行緒命名適合用來識別感興趣的執行緒**執行緒**執行中處理序進行偵錯時的視窗。 具有名為執行緒也可以很有幫助執行透過損毀傾印的檢查和分析效能會擷取使用各種工具，事後進行偵錯時。

## <a name="ways-to-set-a-thread-name"></a>如何設定執行緒名稱

有兩種方式可設定執行緒名稱。 第一個是透過[SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription)函式。 第二個是藉由 Visual Studio 偵錯工具附加至處理程序時，擲回特定例外狀況。 每一種方法有優點和注意事項。

值得注意的是，_兩者_方法可以一起使用，如有需要，因為它們的運作機制是彼此獨立。

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>藉由設定執行緒名稱 `SetThreadDescription`

優點：
* 在 Visual Studio 中，不論偵錯工具已附加至處理序在 SetThreadDescription 會叫用的時間進行偵錯時，會顯示執行緒名稱。
* 執行事後載入 Visual Studio 中的損毀傾印偵錯時，會顯示執行緒名稱。
* 執行緒名稱也會顯示當您使用其他工具中，這類[WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools)偵錯工具和有[Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer)效能分析器。

警告：
* 執行緒名稱只會顯示在 Visual Studio 2017 15.6 版和更新版本的。
* 當事後進行偵錯損毀傾印檔案時，則執行緒名稱才看得到，如果損毀在 Windows 10 1607年版、 Windows Server 2016 或更新版本的 Windows 上建立。

*範例：*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>藉由擲回例外狀況設定執行緒名稱

在程式中設定執行緒名稱的另一種方式是藉由擲回特別設定的例外狀況，Visual Studio 偵錯工具通訊所需的執行緒名稱。

優點：
* 適用於所有版本的 Visual Studio。

警告：
* 僅適用於偵錯工具附加至例外狀況為基礎的方法使用的時間。
* 使用這個方法來設定執行緒名稱在傾印或效能分析工具將無法使用。

*範例：*

`SetThreadName`如下所示的函式示範此例外狀況為基礎的方法。 請注意，執行緒名稱會自動複製到執行緒，以便針對記憶體`threadName`參數可在釋放之後`SetThreadName`呼叫完成。

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>另請參閱
- [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
- [如何：在 Managed 程式碼碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)
