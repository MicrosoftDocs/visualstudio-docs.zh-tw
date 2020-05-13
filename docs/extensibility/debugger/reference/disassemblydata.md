---
title: 拆解資料 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737279"
---
# <a name="disassemblydata"></a>DisassemblyData
描述要顯示的整合式開發環境 (IDE) 的一個拆解指令。

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
DISASSEMBLY_STREAM_FIELDS[常](../../../extensibility/debugger/reference/disassembly-stream-fields.md)量,用於指定填寫哪些欄位。

`bstrAddress`\
位址作為某個起點的偏移量(通常是關聯函數的開頭)。

`bstrCodeBytes`\
此指令的代碼位元組。

`bstrOpcode`\
此指令的操作碼。

`bstrOperands`\
此指令的操作數。

`bstrSymbol`\
與地址關聯的符號名稱(如果有)(公共符號、標籤等)。

`uCodeLocationId`\
此拆解行的代碼位置識別碼。 如果一行的代碼上下文位址大於另一行的代碼上下文位址,則第一行的拆解代碼位置標識符也將大於第二行的代碼位置標識符。

`posBeg`\
對應於開始拆解數據的文件中的位置的[TEXT_POSITION。](../../../extensibility/debugger/reference/text-position.md)

`posEnd`\
對應於分解資料結束文檔中位置的[TEXT_POSITION。](../../../extensibility/debugger/reference/text-position.md)

`bstrDocumentUrl`\
對於可以表示為檔名的文本文檔,使用`bstrDocumentUrl``file://file name`格式填充該欄位,其中可以找到源。

對於不能表示為檔名的文本文檔`bstrDocumentUrl`, 是文檔的唯一標識符,調試引擎必須實現[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)方法。

此欄位還可以包含有關校驗和的其他資訊。 有關詳細資訊,請參閱備註。

`dwByteOffset`\
指令的位元組數是從代碼行的開頭開始的。

`dwFlags`\
指定哪些標誌處於活動狀態[的DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)常量。

## <a name="remarks"></a>備註
每個`DisassemblyData`結構描述一個拆解指令。 這些結構的陣列從[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法返回。

[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構僅用於基於文本的文檔。 此指令的原始程式碼範圍僅針對從語句或行生成的第一個指令(例如,`dwByteOffset == 0`當時 )填寫。

對於非文字文件,可以從代碼獲取文檔上下文`bstrDocumentUrl`, 並且該欄位應為 null 值。 如果`bstrDocumentUrl`欄位與前`bstrDocumentUrl``DisassemblyData`一陣列元素中的欄位相同,`bstrDocumentUrl`則將設置為 null 值。

如果`dwFlags`欄位設置`DF_DOCUMENT_CHECKSUM`了標誌,則其他校驗和資訊將遵循欄位指向`bstrDocumentUrl`的字串。 具體而言,在空字串終止符之後,後面跟著一個 GUID 標識校驗和演演演算法,該演演演算法依次是 4 位元組值,指示校驗和中的位元數,然後依次為校驗和位元組。 請參閱本主題中有關如何編碼和解碼此欄位[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]的示例。

## <a name="example"></a>範例
如果`bstrDocumentUrl`設定了標誌`DF_DOCUMENT_CHECKSUM`, 則該欄位可以包含字串以外的其他資訊。 創建和讀取此編碼字串的過程在 中[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]非常簡單。 但是,在[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]中,這是另一回事。 對於好奇的人,下面的示例顯示了從[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]創建編碼字串的一種方法和在 中[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]解碼編碼字串的一種方法。

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
- [讀](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
