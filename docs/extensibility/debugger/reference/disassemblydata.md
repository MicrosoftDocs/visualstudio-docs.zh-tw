---
title: DisassemblyData |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4276009244f1d49b89311d5d158a34bebf3fcf23
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="disassemblydata"></a>DisassemblyData
描述一個反組譯碼指令整合式的開發環境 (IDE) 以顯示。  
  
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
 從某個起點 （通常是相關聯的函式的開頭） 的位移為位址。  
  
 `bstrCodeBytes`  
 針對這個指令程式碼位元組。  
  
 `bstrOpcode`  
 這個指令的 opcode。  
  
 `bstrOperands`  
 這個指令的運算元。  
  
 `bstrSymbol`  
 符號名稱，如果有的話，與相關聯的位址 （公用符號、 標籤和等等）。  
  
 `uCodeLocationId`  
 此行反組譯程式碼位置識別項。 是否大於另一個程式碼內容位址中一行的程式碼內容位址，然後反組譯的碼的第一個位置識別碼也會大於第二個程式碼位置識別項。  
  
 `posBeg`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)對應至文件中的位置反組譯碼資料開始處。  
  
 `posEnd`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)對應至文件中的反組譯碼資料結束的位置。  
  
 `bstrDocumentUrl`  
 可以表示為檔案名稱的文字文件`bstrDocumentUrl`欄位填入檔案名稱，其中可以找到來源，使用格式`file://file name`。  
  
 無法表示為檔案名稱的文字文件`bstrDocumentUrl`是文件的唯一識別碼和偵錯引擎必須實作[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)方法。  
  
 這個欄位也可以包含總和檢查碼的其他資訊。 如需詳細資訊，請參閱 < 備註 >。  
  
 `dwByteOffset`  
 指令是從程式碼行開頭的位元組數目。  
  
 `dwFlags`  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)常數，指定所使用的旗標。  
  
## <a name="remarks"></a>備註  
 每個`DisassemblyData`結構描述反組譯碼的一個指令。 這些結構的陣列會傳回從[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法。  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構用於以文字為基礎的文件。 此指示的來源的程式碼範圍填寫僅適用於從陳述式或列，例如產生的第一個指令，當`dwByteOffset == 0`。  
  
 可從程式碼，取得非文字的文件，文件內容和`bstrDocumentUrl`欄位應為 null 的值。 如果`bstrDocumentUrl`欄位等同於`bstrDocumentUrl`欄位在舊版`DisassemblyData`陣列項目，然後設定`bstrDocumentUrl`為 null 值。  
  
 如果`dwFlags`欄位具有`DF_DOCUMENT_CHECKSUM`旗標設定，其他的總和檢查碼資訊如下所指向的字串`bstrDocumentUrl`欄位。 具體而言，null 字串結束字元之後那里遵循識別總和檢查碼演算法，依次後面 4 位元組值，指出總和檢查碼中的位元組數目，而且，依次後面的總和檢查碼位元組的 GUID。 如何編碼和解碼的欄位中，請參閱本主題的範例[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]。  
  
## <a name="example"></a>範例  
 `bstrDocumentUrl`欄位只能包含字串以外的其他資訊，如果`DF_DOCUMENT_CHECKSUM`旗標設定。 建立和讀取此編碼的字串的程序是直接在[!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]。 不過，在[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]，它是另一個主題。 那些好奇，如下列範例會示範如何建立編碼的字串，從[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]和其中一種方式來解碼的編碼的字串中[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]。  
  
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
  
               // Parse string out.  String is assumed to be Unicode.  
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
 [讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
