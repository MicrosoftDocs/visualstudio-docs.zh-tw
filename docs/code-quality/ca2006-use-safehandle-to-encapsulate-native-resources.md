---
title: CA2006： 使用 SafeHandle 封裝原生資源 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0fdef78fdad92eb08012a474afff5c4c8c4d7ab8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006：使用 SafeHandle 封裝原生資源
|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|分類|Microsoft.Reliability|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 Managed 程式碼使用<xref:System.IntPtr>存取原生資源。  
  
## <a name="rule-description"></a>規則描述  
 使用`IntPtr`在 managed 程式碼可能表示有潛在的安全性和可靠性問題。 所有使用`IntPtr`必須檢視，以決定是否使用<xref:System.Runtime.InteropServices.SafeHandle>，或類似的技術，需要在該處。 如果將會發生問題`IntPtr`代表某些原生資源，例如記憶體、 檔案控制代碼或通訊端，managed 程式碼會被視為擁有。 如果 managed 程式碼擁有的資源，它也必須釋放與它相關聯的原生資源因為若要這樣做會造成資源流失。  
  
 在這種情況下，安全性或可靠性會也存在問題如果允許多執行緒的存取`IntPtr`和釋出資源所代表的方式`IntPtr`提供。 這些問題牽涉到回收`IntPtr`時正在進行另一個執行緒上同時使用的資源，資源釋放值。 這可能會造成競爭情形，其中一個執行緒可以讀取或寫入錯誤的資源相關聯的資料。 例如，如果您的型別會儲存為將 OS 控制代碼`IntPtr`並允許使用者同時呼叫**關閉**和任何其他方法，會使用該控制代碼，同時並沒有某種類型的同步處理，您的程式碼已回收的控制代碼發生問題。  
  
 此回收問題的控制代碼可能會導致資料損毀，通常有安全性弱點。 `SafeHandle` 和其同層級類別<xref:System.Runtime.InteropServices.CriticalHandle>提供機制來封裝資源的原生控制代碼，讓您可以避免這類執行緒的問題。 此外，您可以使用`SafeHandle`和其同層級類別`CriticalHandle`的其他執行緒的問題，例如，若要小心控制對原生方法的呼叫中包含的原生控制代碼複本的 managed 物件的存留期。 在此情況下，您經常可以移除呼叫`GC.KeepAlive`。 當您使用您帶來的效能負擔 thay`SafeHandle`和壓縮的程度， `CriticalHandle`，通常可以透過謹慎設計降低。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 轉換`IntPtr`使用量`SafeHandle`，安全管理原生資源的存取權。 請參閱<xref:System.Runtime.InteropServices.SafeHandle>參考主題的範例。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 您不應該隱藏這個警告。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IDisposable>