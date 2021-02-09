---
title: MarkProfile | Microsoft Docs
description: MarkProfile 方法會在 .vsp 檔案中插入設定檔標記。 包含 MarkProfile 函式之執行緒的分析必須是 ON，才能插入標記。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b4e66049ec5547913dad8df7256f2db3d2395fa0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851955"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile` 方法會在 .*vsp* 檔案中插入分析標記。 包含 `MarkProfile` 函式之執行緒的分析必須設定為 ON，才能插入標記。

## <a name="syntax"></a>語法

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>參數
 `lMarker`

 要插入的標記。 標記必須大於或等於 0 (零)。

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 此函式會使用 **PROFILE_COMMAND_STATUS** 列舉來指出成功或失敗。 傳回值可以是下列其中一個：

|列舉值|Description|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|參數小於或等於 0。 會保留這些值。 不會記錄標記和註解。|
|MARK_ERROR_MODE_NEVER|呼叫函式時，分析模式設定為 NEVER。 不會記錄標記和註解。|
|MARK_ERROR_MODE_OFF|呼叫函式時，分析模式設定為 OFF。 不會記錄標記和註解。|
|MARK_ERROR_NO_SUPPORT|在此內容中不支援任何標記。 不會記錄標記和註解。|
|MARK_ERROR_OUTOFMEMORY|沒有記憶體可供記錄事件。 不會記錄標記和註解。|
|MARK_TEXTTOOLONG|字串超出 256 個字元的長度上限。 會將註解字串截斷，並且記錄標記和註解。|
|MARK_OK|會傳回 MARK_OK 以表示作業成功。|

## <a name="remarks"></a>備註
 如果要對包含 MarkProfile 函式的執行緒進行分析，則每次程式碼執行時，都會將標記值插入到 .*vsp* 檔案中。 您可以呼叫 MarkProfile 多次。

 分析標記屬於全域範圍。 例如，在一個執行緒中插入的分析標記，可用來標記 .*vsp* 檔案中任何執行緒之資料區段的開頭或結尾。

 使用 Mark 命令或 API 函式 (CommentMarkAtProfile、CommentMarkProfile 或 MarkProfile) 來插入標記和註解時，包含標記分析函式之執行緒的分析狀態必須設定為開啟。

> [!IMPORTANT]
> MarkProfile 方法應該只與檢測分析方法搭配使用。

## <a name="net-framework-equivalent"></a>.NET Framework 同等
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>函式資訊
 標頭：在 *VSPerf.h* 中宣告

 匯入程式庫：*VSPerf.lib*

## <a name="example"></a>範例
 下列程式碼說明 MarkProfile 函式。

```cpp
void ExerciseMarkProfile()
{
    // Declare and initialize variables to pass to
    // MarkProfile.  The values of these parameters
    // are assigned based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variables are assigned arbitrary values.
    int markId = 03;

    // Declare enumeration to hold return value of
    // call to MarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    markResult = MarkProfile(markId);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("MarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>另請參閱
- [Visual Studio profiler API 參考 (原生) ](../profiling/visual-studio-profiler-api-reference-native.md)
