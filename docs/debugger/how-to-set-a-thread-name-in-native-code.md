---
title: 如何：在原生程式碼中設定執行緒名稱 |Microsoft Docs
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
ms.openlocfilehash: a89dce28f33bef0ffdb13d6254b2ac6b86ac25db
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589027"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>如何：在機器碼中設定執行緒名稱
在所有 Visual Studio 版本中，都可以將執行緒命名。 執行緒命名有助於在偵錯工具執行中的進程時，識別 [**執行緒**] 視窗中感興趣的執行緒。 當透過損毀傾印檢查和使用各種工具來分析效能捕捉時，擁有 recognizably 名稱的執行緒也會很有説明。

## <a name="ways-to-set-a-thread-name"></a>設定執行緒名稱的方式

有兩種方式可以設定執行緒名稱。 第一個是透過[SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription)函數。 第二種方式是在 Visual Studio 偵錯工具附加至進程時擲回特定的例外狀況。 每種方法都有其優點和注意事項。 從 Windows 10 1607 版或 Windows Server 2016 開始，支援使用 `SetThreadDescription`。

值得注意的是，如果有需要，_這兩_種方法都可以一起使用，因為它們的工作機制彼此獨立。

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>使用 `SetThreadDescription` 設定執行緒名稱

優點：
* 在 Visual Studio 中進行調試時，不論偵錯工具是否附加至進程（在叫用 SetThreadDescription 時），都會顯示執行緒名稱。
* 藉由在 Visual Studio 中載入損毀傾印來執行事後剖析後的偵錯工具時，會顯示執行緒名稱。
* 使用其他工具（例如[WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools)偵錯工具和[Windows performance analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer)效能分析器）時，也會顯示執行緒名稱。

警告：
* 只有在 Visual Studio 2017 15.6 版和更新版本中，才會顯示執行緒名稱。
* 在事後剖析錯損毀傾印檔案時，只有當損毀是在 Windows 10 1607 版、Windows Server 2016 或更新版本的 Windows 上建立時，才會顯示執行緒名稱。

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>藉由擲回例外狀況來設定執行緒名稱

在程式中設定執行緒名稱的另一種方式，是藉由擲回特別設定的例外狀況，將所需的執行緒名稱傳達給 Visual Studio 偵錯工具。

優點：
* 適用于所有版本的 Visual Studio。

警告：
* 只有在使用以例外狀況為基礎的方法時附加偵錯工具時，才會運作。
* 使用此方法設定的執行緒名稱，將無法在傾印或效能分析工具中使用。

*範例：*

下面所示的 `SetThreadName` 函式示範此以例外狀況為基礎的方法。 請注意，執行緒名稱將會自動複製到執行緒，以便在完成 `SetThreadName` 呼叫之後，可以釋放 `threadName` 參數的記憶體。

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

## <a name="see-also"></a>請參閱
- [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
- [如何：在 Managed 程式碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)
