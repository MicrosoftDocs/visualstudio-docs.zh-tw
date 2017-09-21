---
title: "DisassemblyData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisassemblyData"
helpviewer_keywords: 
  - "DisassemblyData 結構"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

描述一個整合式的開發環境 \(IDE\) 若要顯示的反組譯碼指令。  
  
## 語法  
  
```cpp#  
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
  
```c#  
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
  
## Members  
 `dwFields`  
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)用來指定哪個欄位填寫常數。  
  
 `bstrAddress`  
 位移從某個起點 \(通常是相關的函式的開頭\) 位址。  
  
 `bstrCodeBytes`  
 針對這個指令碼的位元組。  
  
 `bstrOpcode`  
 這個指令的 opcode。  
  
 `bstrOperands`  
 這個指令的運算元。  
  
 `bstrSymbol`  
 符號名稱，如果有的話，與相關聯的位址 \(公用符號、 標籤等等\)。  
  
 `uCodeLocationId`  
 反組譯此行程式碼的位置識別碼。  如果某行的程式碼內容位址大於另一個程式碼內容位址，然後反組譯的碼位置識別項的第一個也會大於第二個程式碼的位置識別碼。  
  
 `posBeg`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) ，相對於文件中的反組譯碼資料的起始處的位置。  
  
 `posEnd`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) ，相對於文件中的反組譯碼資料的結束處的位置。  
  
 `bstrDocumentUrl`  
 可以表示為檔名的文字文件`bstrDocumentUrl`何處可以找到來源，檔名中填寫欄位使用格式`部份名稱`。  
  
 無法以檔名的文字文件`bstrDocumentUrl`是文件的唯一識別項，並且偵錯引擎必須實作[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)方法。  
  
 這個欄位也可以包含加總檢查碼的其他資訊。  如需詳細資訊，請參閱 「 備註 」。  
  
 `dwByteOffset`  
 指令是從程式碼行開頭的位元組數目。  
  
 `dwFlags`  
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)指定的旗標為作用中的常數。  
  
## 備註  
 每個`DisassemblyData`結構描述的反組譯碼的一個指令。  這些結構的陣列傳回的[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法。  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)結構用於文字基礎僅有文件。  針對這個指令碼範圍填寫只對第一個指令所產生的陳述式或線條，比方說，當`dwByteOffset == 0`。  
  
 對於非文字的文件，文件內容可避免惡意程式碼，以及`bstrDocumentUrl`欄位應該是空值。  如果`bstrDocumentUrl`欄位等同於`bstrDocumentUrl`欄位在先前的`DisassemblyData`陣列元素，則設定`bstrDocumentUrl`設為 null 值。  
  
 如果`dwFlags`欄位具有`DF_DOCUMENT_CHECKSUM`再額外加總檢查碼資訊如下的字串所指的旗標集， `bstrDocumentUrl`欄位。  具體而言，null 字串結束字元之後那里遵循，依序且後面跟著 4 個位元組值，指出加總檢查碼位元組數，依序時，接著加總檢查碼位元組的加總檢查碼演算法用來識別的 GUID。  有關如何進行編碼和解碼的欄位中，請參閱本主題中的範例[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]。  
  
## 範例  
 `bstrDocumentUrl`欄位可以包含字串以外的其他資訊，如果`DF_DOCUMENT_CHECKSUM`旗標設。  建立及讀取此編碼的字串的程序相當簡單，在[!INCLUDE[vcprvc](../../../debugger/includes/vcprvc_md.md)]。  不過，在[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]，這是另外一回事。  對新手而言好奇，下列範例會示範建立編碼的字串，從一種方式[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]和單向解碼已編碼的字串，在[!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]。  
  
```c#  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
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
            for (int i = 0; i < guidDataLength; i++)  
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
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
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
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)