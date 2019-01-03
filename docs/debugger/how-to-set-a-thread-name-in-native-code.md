---
title: HOW TO：在機器碼中設定執行緒名稱 |Microsoft Docs
ms.custom: ''
ms.date: 12/17/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9226e009936d0a644a5a6fcfcaba57bc3af25d7d
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803094"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>HOW TO：在機器碼中設定執行緒名稱
在所有 Visual Studio 版本中，都可以將執行緒命名。 將執行緒命名後，在 [執行緒] 視窗中追蹤執行緒會很方便。

## <a name="set-a-thread-name"></a>設定執行緒名稱

`SetThreadName`函式很適合用於設定和檢視執行緒，如果偵錯工具附加至您執行的程式碼。 從 Visual Studio 2017 15.6 版中，您可以使用[SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription)函式來設定並檢視執行緒的名稱。

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

## <a name="set-a-thread-name-using-setthreadname"></a>設定使用 SetThreadName 執行緒名稱

若要在程式中設定執行緒名稱，您也可以使用`SetThreadName`函式，如下列程式碼範例所示。 請注意，執行緒名稱會複製到執行緒，以便釋放 `threadName` 參數的記憶體。  這個方法會使用例外狀況為基礎的方法，僅適用於偵錯工具附加至例外狀況為基礎的方法使用的時間。 您使用這個方法來設定執行緒名稱在傾印或效能分析工具將無法使用。

下列程式碼範例示範如何使用`SetThreadName`:

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
 [對多執行緒應用程式進行偵錯](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)   
 [如何：在 Managed 程式碼碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)