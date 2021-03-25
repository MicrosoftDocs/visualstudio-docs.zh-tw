---
title: 結構和等位 |Microsoft Docs
description: 本文將連結至 Visual Studio 偵錯工具中結構和等位的參考描述。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 055c8972643a94bd8f13aa6e5e6bc5dde600140b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061468"
---
# <a name="structures-and-unions"></a>Structures and Unions
以下是 Visual Studio 調試 SDK 中的結構和等位。

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 指定處理序識別碼，此識別碼可能是系統識別碼或 GUID。

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 描述將引發中斷點的條件。

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 描述錯誤中斷點的解決方式，包括位置、程式和執行緒。

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 指定用來描述中斷點位置的結構類型。

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) 定義元件，以描述程式碼中位址的中斷點位置。

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) 描述直接系結至要進行偵錯工具之位址的中斷點位置。

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 描述程式碼原始程式檔中的中斷點位置。

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 描述程式碼中函式之中斷點的位移位置。

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) 用來根據使用者可從 IDE 輸入的字串來設定程式碼中斷點。

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) 用於設定資料中斷點，這些中斷點是以使用者可從 IDE 輸入的字串為基礎。

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) 描述中斷點在特定位置的解決方式。

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 描述在先前傳遞中斷點之後，將引發中斷點的計數和條件。

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 包含執行中斷點所需的資訊。

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 包含執行中斷點所需的資訊 (與 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 結構相同，但包含) 的廠商 GUID、條件約束和追蹤點資訊。

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) 描述程式碼中斷點的位置。

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 描述系結資料中斷點的結果。

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 描述程式碼中斷點或資料中斷點的系結中斷點資訊。

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 指定中斷點解析位置的結構。

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) 描述字串的陣列。

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 指定取自中繼資料之欄位型別的相關資訊。

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) 描述函數或方法的呼叫。

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) 描述正在執行偵錯工具的電腦。

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) 描述 Guid 清單。

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 描述記憶體內容或程式碼內容。

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 描述正在進行調試的程式中的位址。

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 代表許多不同種類的位址之一。

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 識別自訂檢視器或型別視覺化檢視。

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 描述 debug 屬性，此屬性會接著描述具有名稱、類型和值之階層式本質的物件。

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 描述參考。

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 描述要顯示的 IDE 反組譯。

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 描述正在進行調試的程式擲回的例外狀況或執行階段錯誤。

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 描述本機變數、參數或其他欄位。

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 描述堆疊框架。

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) 描述可用的偵錯工具引擎之唯一識別碼陣列。

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) 用來設定模組的 JustMyCode 資訊。

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) 描述特定的電腦。

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 描述陣列中的陣列元素。

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 描述類別或結構的欄位位址。

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 描述範圍內的區域變數位址 (通常是) 的函式或方法。

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 描述類別的方法位址。

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 描述方法或函數的參數。

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 描述方法或函數的傳回值。

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 描述取自中繼資料的欄位類型。

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 描述 (DLL、EXE 或元件) 的特定模組。

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 描述已搜尋之符號搜尋路徑的相關狀態資訊。

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 描述原生位址。

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) 描述取自 PDB 符號的欄位類型。

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) 描述準備系結至程式碼位置之中斷點的狀態。

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 描述處理常式。

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) 描述代表程式節點的 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 物件清單。

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 描述在電腦上執行的處理常式。

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 描述指定文字中的行和資料行位置。

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 描述執行緒的屬性。

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 描述欄位的類型。

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 描述實體位址。

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 描述相對於 `this` Visual Basic) 中指標 (的位址 `Me` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg .h、sh. h 或 ee

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
