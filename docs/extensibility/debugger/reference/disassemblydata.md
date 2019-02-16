---
title: DisassemblyData |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bbc61236156cdcbfacdf73101752ea6811470c0
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317439"
---
# <a name="disassemblydata"></a>DisassemblyData
描述一個反組譯碼指令的整合式的開發環境 (IDE) 來顯示。

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
`dwFields`  
[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)指定哪些欄位都已填寫的常數。

`bstrAddress`  
從某個起點 （通常是相關聯的函式的開頭） 的位移位址。

`bstrCodeBytes`  
此指令程式碼位元組。

`bstrOpcode`  
這個指示 opcode。

`bstrOperands`  
這個指令的運算元。

`bstrSymbol`  
符號名稱，如果有的話，與相關聯的位址 （公用符號、 標籤和等等）。

`uCodeLocationId`  
反組譯此行程式碼位置識別碼。 如果一行的程式碼內容位址大於另一個程式碼內容位址，然後反組譯程式碼位置識別碼的第一個也會大於第二個程式碼位置識別碼。

`posBeg`  
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) ，其對應於文件中的反組譯碼資料的開始處的位置。

`posEnd`  
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) ，其對應於文件中的反組譯碼資料的結束位置的位置。

`bstrDocumentUrl`  
可以表示為檔案名稱的文字文件`bstrDocumentUrl`欄位會填入檔案名稱，您可以找到來源，使用格式`file://file name`。

無法為檔案名稱，表示文字文件`bstrDocumentUrl`是文件的唯一識別碼，而且必須實作的偵錯引擎[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)方法。

此欄位也可以包含總和檢查碼的其他資訊。 如需詳細資訊，請參閱 < 備註 >。

`dwByteOffset`  
指令會從程式碼行開頭的位元組數目。

`dwFlags`  
[DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)指定的旗標都是作用中的常數。

## <a name="remarks"></a>備註
每個`DisassemblyData`結構描述反組譯碼的一個指令。 這些結構的陣列會傳回從[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法。

[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構可用來以文字為基礎的文件。 此指令的來源的程式碼範圍填妥只針對從陳述式或列，例如產生的第一個指令，當`dwByteOffset == 0`。

對於非文字的文件，文件內容可從此程式碼，而`bstrDocumentUrl`欄位應為 null 的值。 如果`bstrDocumentUrl`欄位是相同`bstrDocumentUrl`欄位中先前`DisassemblyData`陣列項目，然後設定`bstrDocumentUrl`null 值。

如果`dwFlags`欄位都`DF_DOCUMENT_CHECKSUM`加上旗標集，則其他的總和檢查碼資訊如下所指向的字串`bstrDocumentUrl`欄位。 具體而言，null 字串結束字元之後那里遵循用來識別，進而後面 4 位元組值，指出總和檢查碼中的位元組數目，而且，依序且後面跟著的總和檢查碼位元組的總和檢查碼演算法的 GUID。 如何編碼和解碼的欄位中，請參閱本主題的範例[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]。

## <a name="example"></a>範例
`bstrDocumentUrl`欄位只能包含字串以外的其他資訊，如果`DF_DOCUMENT_CHECKSUM`旗標設定。 建立和讀取此編碼的字串的程序相當簡單[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]。 不過，在[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]，它是另一回事。 對於使用者而言很好奇，下列範例會示範如何建立編碼的字串，從[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]其中一種方式來解碼的編碼的字串和[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]。

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
[結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)  
[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)  
[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)  
[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)  
[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)  
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
[DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
