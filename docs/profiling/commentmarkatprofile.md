---
title: CommentMarkAtProfile | Microsoft Docs
description: 您可以使用 CommentMarkAtProfile 方法，將時間戳記值、數位標記和批註字串插入 .vsp 檔案中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b40620388ffb3aefcd77eeb3f60355ed293ea59d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970565"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
方法會在 .vsp 檔案中 `CommentMarkAtProfile` 插入時間戳記值、數位標記和批註字串。  時間戳記值可以用來同步處理外部事件。 針對要插入的標記和註解，包含 CommentMarkAtProfile 函式之執行緒的分析必須是 ON。

## <a name="syntax"></a>語法

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>參數
 `dnTimestamp`

 代表時間戳記值的 64 位元整數。

 `lMarker`

 要插入的數字標記。 標記必須大於或等於 0 (零)。

 `szComment`

 要插入之文字字串的指標。 此字串必須小於 256 個字元 (包含 NULL 結束字元)。

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
 使用 Mark 命令或 API 函式 (CommentMarkAtProfile、CommentMarkProfile 或 MarkProfile) 來插入標記和註解時，包含標記分析函式之執行緒的分析狀態必須設定為開啟。 分析標記屬於全域範圍。 例如，在一個執行緒中插入的分析標記，可用來標記 .vsp 檔案中任何執行緒之資料區段的開頭或結尾。

> [!IMPORTANT]
> CommentMarkAtProfile 方法只應該與檢測搭配使用。

## <a name="net-framework-equivalent"></a>.NET Framework 同等
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>函式資訊

|Item|值|
|-|-|
|**標頭**|包含 *VSPerf.h*|
|**程式庫**|使用 *VSPerf.lib*|
|**Unicode**|實作為 CommentMarkAtProfileW (Unicode) 和 CommentMarkAtProfileA (ANSI)。|

## <a name="example"></a>範例
 下列程式碼說明如何使用 CommentMarkAtProfile 泛型函式呼叫。 此範例假設使用 Win32 字串巨集以及 ANSI 的編譯器設定，來判斷程式碼是否呼叫啟用 ANSI 功能的函式。

```cpp
void ExerciseCommentMarkAtProfile(void)
{
    // Declare and initalize variables to pass to
    // CommentMarkAtProfile.  The values of these
    // parameters are assigned based on the needs
    // of the code; and for the sake of simplicity
    // in this example, the variables are assigned
    // arbitrary values.
    int64 timeStamp = 0x1111;
    long markId = 01;
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare MarkOperationResult Enumerator.
    // Holds return value from call to CommentMarkAtProfile.
    PROFILE_COMMAND_STATUS markResult;

    markResult = CommentMarkAtProfile(
        timeStamp,
        markId,
        markText);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
    pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>另請參閱
- [Visual Studio Profiler API 參考 (原生) ](../profiling/visual-studio-profiler-api-reference-native.md)
