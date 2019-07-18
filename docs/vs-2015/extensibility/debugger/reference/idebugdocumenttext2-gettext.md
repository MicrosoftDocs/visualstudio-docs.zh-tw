---
title: IDebugDocumentText2::GetText |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 066c2c025fe7b1c83fb30cb3a0e1a7b61d8c2c41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200186"
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從指定之位置的文件中擷取的文字。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetText(   
   TEXT_POSITION pos,  
   ULONG         cMaxChars,  
   WCHAR*        pText,  
   ULONG*        pcNumChars  
);  
```  
  
```csharp  
int GetText(   
   eumn_TEXT_POSITION pos,  
   uint               cMaxChars,  
   IntPtr             pText,  
   out uint           pcNumChars  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pos`  
 [in]A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)結構，表示要擷取文字的位置。  
  
 `cMaxChars`  
 [in]要擷取的文字字元的數目上限。  
  
 `pText`  
 [in、 out]要被填入所需的文字緩衝區的指標。 這個緩衝區必須至少包含`cMaxChars`寬字元數。  
  
 `pcNumChars`  
 [out]傳回實際擷取的字元的數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="example"></a>範例  
 這個範例會示範如何從 C# 呼叫這個方法。  
  
```csharp  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace Mynamespace  
{  
    class MyClass  
    {  
         string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)  
        {  
             string documentText = string.Empty;  
             if (pText != null)  
             {  
                  uint numLines = 0;  
                  uint numChars = 0;  
                  int hr;  
                  hr = pText.GetSize(ref numLines, ref numChars);  
                  if (ErrorHandler.Succeeded(hr))  
                  {  
                       IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));  
                       uint actualChars = 0;  
                       hr = pText.GetText(pos, numChars, buffer, out actualChars);  
                       if (ErrorHandler.Succeeded(hr))  
                       {  
                            documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);  
                       }  
                       Marshal.FreeCoTaskMem(buffer);  
                  }  
              }  
              return documentText;  
         }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
