---
description: 描述要顯示之整合式開發環境 (IDE) 的一個反組解碼指令。
title: DisassemblyData |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71d52c4f48f23368d83d81f88fba4bf0ba36f197
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096118"
---
# <a name="disassemblydata"></a>DisassemblyData
描述要顯示之整合式開發環境 (IDE) 的一個反組解碼指令。

## <a name="syntax"></a>語法

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>成員
`dwFields`\
[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)常數，指定要填寫的欄位。

`bstrAddress`\
從某個起點開始的位址，通常是關聯函數) 的開頭 (。

`bstrCodeBytes`\
此指令的程式碼位元組。

`bstrOpcode`\
此指令的 opcode。

`bstrOperands`\
此指令的運算元。

`bstrSymbol`\
與位址相關聯的符號名稱（如果有的話） (公用符號、標籤等等) 。

`uCodeLocationId`\
此拆解行的程式碼位置識別碼。 如果一行的程式碼內容位址大於另一個行的程式碼內容位址，則第一個行的反組譯程式碼位置識別碼也會大於第二行的程式碼位置識別碼。

`posBeg`\
對應至檔中反組解碼資料開始位置的 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 。

`posEnd`\
對應于檔中反組解碼資料結束位置的 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 。

`bstrDocumentUrl`\
若為可以檔案名表示的文字檔， `bstrDocumentUrl` 欄位會填入可找到來源的檔案名，並使用格式 `file://file name` 。

對於無法以檔案名表示的文字檔，是檔的 `bstrDocumentUrl` 唯一識別碼，而且 debug engine 必須執行 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) 方法。

此欄位也可包含總和檢查碼的其他相關資訊。 如需詳細資訊，請參閱備註。

`dwByteOffset`\
指令從程式程式碼的開頭算起的位元組數目。

`dwFlags`\
[DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)常數，指定使用中的旗標。

## <a name="remarks"></a>備註
每個結構都描述一個反組解碼 `DisassemblyData` 指令。 從 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 方法傳回這些結構的陣列。

[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構僅用於以文字為基礎的檔。 此指令的原始程式碼範圍只會填入語句或程式列所產生的第一個指令，例如，when `dwByteOffset == 0` 。

若為非文字檔，則可以從程式碼中取得檔內容，而且 `bstrDocumentUrl` 欄位應為 null 值。 如果 `bstrDocumentUrl` 欄位與 `bstrDocumentUrl` 上一個陣列元素中的欄位相同 `DisassemblyData` ，則將設定 `bstrDocumentUrl` 為 null 值。

如果 `dwFlags` 欄位已 `DF_DOCUMENT_CHECKSUM` 設定旗標，則會在欄位所指向的字串後面加上其他總和檢查碼資訊 `bstrDocumentUrl` 。 具體而言，在 null 字串結束字元之後，會有可識別總和檢查碼演算法的 GUID，後面接著4位元組值，指出總和檢查碼中的位元組數目，然後再接著總和檢查碼位元組。 請參閱本主題中的範例，以瞭解如何在中編碼和解碼此欄位 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] 。

## <a name="example"></a>範例
`bstrDocumentUrl`如果設定了旗標，欄位可以包含字串以外的其他資訊 `DF_DOCUMENT_CHECKSUM` 。 在中，建立和讀取此編碼字串的程式很簡單 [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] 。 不過，在中 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] ，這也是另一種方式。 針對好奇的人，下列範例示範從建立編碼字串的方法， [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] 以及在中解碼編碼字串的一種方式 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] 。

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
