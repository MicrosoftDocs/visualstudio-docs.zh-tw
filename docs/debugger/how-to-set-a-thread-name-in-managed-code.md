---
title: "如何：在 Managed 程式碼中設定執行緒名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], 執行緒"
  - "執行緒名稱"
  - "Thread.Name 屬性"
  - "執行緒處理 [Visual Studio], 名稱"
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# 如何：在 Managed 程式碼中設定執行緒名稱
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在所有 Visual Studio 版本中，都可以將執行緒命名。  將執行緒命名後，在 \[**執行緒**\] 視窗中追蹤執行緒會很方便。  因為 Visual Studio Express 版本並不提供 \[**執行緒**\] 視窗，所以將執行緒命名，在 Express 版本中不太有用。  
  
 若要在 Managed 程式碼內設定執行緒名稱，請使用 <xref:System.Threading.Thread.Name%2A> 屬性。  
  
## 範例  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## 請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在機器碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-native-code.md)