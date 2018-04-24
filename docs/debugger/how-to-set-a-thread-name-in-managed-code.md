---
title: 如何： 在 Managed 程式碼中設定執行緒名稱 |Microsoft 文件
ms.custom: ''
ms.date: 04/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 39a732f691cbed525e853d74b5cf4e4abb55eb47
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>如何：在 Managed 程式碼中設定執行緒名稱
在所有 Visual Studio 版本中，都可以將執行緒命名。 執行緒命名可用於追蹤的執行緒中的**執行緒**視窗。
  
 若要在 Managed 程式碼內設定執行緒名稱，請使用 <xref:System.Threading.Thread.Name%2A> 屬性。  
  
## <a name="example"></a>範例  

```csharp
public class Needle
{
    // This method will be called when the thread is started.  
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.   
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".  
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate  
    oThread.Start();
}
```

```VB 
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
    ' Set the Thread name to "MyThread".  
    oThread.Name = "MyThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [如何：在機器碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-native-code.md)