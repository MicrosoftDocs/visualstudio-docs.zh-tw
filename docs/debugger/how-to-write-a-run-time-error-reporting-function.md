---
title: "如何： 撰寫報告函式的執行階段錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d140606382367d5968871f65034db619fb9325e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-write-a-run-time-error-reporting-function"></a>如何：撰寫執行階段錯誤報告函式
執行階段錯誤的自訂報告函式，它必須具有與 `_CrtDbgReportW` 相同的宣告。 它應該向偵錯工具傳回值 1。  
  
 下列範例顯示如何定義自訂報告函式：  
  
## <a name="example"></a>範例  
  
```  
#include <stdio.h>  
int errorhandler = 0;  
void configureMyErrorFunc(int i)  
{  
    errorhandler = i;  
}  
  
int MyErrorFunc(int errorType, const wchar_t *filename,  
                int linenumber, const wchar_t *moduleName,  
                const wchar_t *format, ...)  
{  
    switch (errorhandler)  
    {  
    case 0:  
    case 1:  
        wprintf(L"Error type %d at %s line %d in %s",  
                errorType, filename, linenumber, moduleName);  
        break;  
    case 2:  
    case 3:  
        fprintf(stderr, "Error type");  
        break;  
    }  
  
    return 1;  
}  
```  
  
## <a name="example"></a>範例  
 下列範例顯示更複雜的自訂報告函式。 在這個範例中，switch 陳述式會處理由 `reportType` 的 `_CrtDbgReportW` 參數所定義的各種錯誤類型。 因為您要正在取代 `_CrtDbgReportW`，所以無法使用 `_CrtSetReportMode`。 您的函式必須處理輸出。 這個函式中的第一個變數引數會接受一個執行階段錯誤碼。 如需詳細資訊，請參閱[_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype)。  
  
```  
#include <windows.h>  
#include <stdarg.h>  
#include <rtcapi.h>  
#include <malloc.h>  
#pragma runtime_checks("", off)  
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,   
                   const wchar_t *module, const wchar_t *format, ...)  
{  
    // Prevent re-entrance.  
    static long running = 0;  
    while (InterlockedExchange(&running, 1))  
        Sleep(0);  
    // Now, disable all RTC failures.  
    int numErrors = _RTC_NumErrors();  
    int *errors=(int*)_alloca(numErrors);  
    for (int i = 0; i < numErrors; i++)  
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);  
  
   // First, get the rtc error number from the var-arg list.  
    va_list vl;  
    va_start(vl, format);  
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);  
    va_end(vl);  
  
    wchar_t buf[512];  
    const char *err = _RTC_GetErrDesc(rtc_errnum);  
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",  
        err,  
        line,  
        file ? file : L"Unknown",  
        module ? module : L"Unknown");  
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;  
    // Now, restore the RTC errortypes.  
    for(int i = 0; i < numErrors; i++)  
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);  
    running = 0;  
    return res;  
}  
#pragma runtime_checks("", restore)  
```  
  
## <a name="example"></a>範例  
 您可以使用 `_RTC_SetErrorFuncW` 來安裝用來代替 `_CrtDbgReportW` 的自訂函式。 如需詳細資訊，請參閱[_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw)。 `_RTC_SetErrorFuncW` 傳回值是先前的報告函式，必要時您可以儲存後再還原。  
  
```  
#include <rtcapi.h>  
int main()  
{  
    _RTC_error_fnW oldfunction, newfunc;  
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);  
    // Run some code.  
    newfunc = _RTC_SetErrorFuncW(oldfunction);  
    // newfunc == &MyErrorFunc;  
    // Run some more code.  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂原生執行階段檢查](../debugger/native-run-time-checks-customization.md)