---
title: 在機器碼中設定執行緒名稱 |Microsoft Docs
description: 在 Visual Studio 中的多執行緒應用程式偵錯工具期間，于機器碼中設定執行緒名稱。 執行緒命名是用來在 [執行緒] 視窗中追蹤執行緒。
ms.custom: SEO-VS-2020
ms.date: 12/17/2018
ms.topic: how-to
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
ms.openlocfilehash: a713b6db074586898ff72cd8595c4cc0d20d99cf
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149517"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>如何：在機器碼中設定執行緒名稱
在所有 Visual Studio 版本中，都可以將執行緒命名。 執行緒命名適用于在偵測執行中的進程時，在 [ **執行緒** ] 視窗中找出感興趣的執行緒。 當您透過損毀傾印檢查，以及使用各種工具來分析效能捕捉時，具有 recognizably 命名的執行緒也會很有説明。

## <a name="ways-to-set-a-thread-name"></a>設定執行緒名稱的方式

有兩種方式可以設定執行緒名稱。 第一個是透過 [>setthreaddescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) 函數。 第二個方法是在 Visual Studio 偵錯工具附加至進程時擲回特定的例外狀況。 每種方法都有其優點和注意事項。 `SetThreadDescription`從 Windows 10、1607版或 Windows Server 2016 開始支援的使用。

值得注意的是， _這兩_ 種方法都可以搭配使用，因為它們的運作機制彼此獨立。

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>使用來設定執行緒名稱 `SetThreadDescription`

優點：
* 在 Visual Studio 中進行偵錯工具時，不論偵錯工具是否在叫用 >setthreaddescription 時附加至進程，都可以看見執行緒名稱。
* 在 Visual Studio 中載入損毀傾印來執行事後剖析後的偵錯工具時，會顯示執行緒名稱。
* 使用其他工具（例如 [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) 偵錯工具和 [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) 效能分析器）時，也會顯示執行緒名稱。

警告：
* 只有在 Visual Studio 2017 15.6 版和更新版本中才會顯示執行緒名稱。
* 事後剖析錯損毀傾印檔案時，只有當損毀是 1607 Windows 10 在 Windows Server 2016 或更新版本的 Windows 上建立時，才會顯示執行緒名稱。

*範例︰*

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
* 只有在使用以例外狀況為基礎的方法時附加偵錯工具時，才適用。
* 使用這個方法所設定的執行緒名稱將無法在傾印或效能分析工具中使用。

*範例︰*

`SetThreadName`下面顯示的函式會示範這個以例外狀況為基礎的方法。 請注意，執行緒名稱將會自動複製到執行緒，因此 `threadName` 可以在呼叫完成之後釋放參數的記憶體 `SetThreadName` 。

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
- [Debug 多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)
- [如何：在 Managed 程式碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)
