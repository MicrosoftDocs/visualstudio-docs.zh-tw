---
title: 如何：使用物件管理員註冊程式庫 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7179bd87fdfd9a2c3fc36958a9d964ec4f790dbd
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905230"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>如何：使用物件管理員註冊程式庫
符號流覽工具，例如**類別檢視**、**物件瀏覽器**、**呼叫瀏覽器**和**尋找符號結果**，可讓您在專案或外部元件中查看符號。 這些符號包括命名空間、類別、介面、方法和其他語言元素。 程式庫會追蹤這些符號，並將其公開至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 物件管理員，以在工具中填入資料。

 物件管理員會持續追蹤所有可用的程式庫。 每個程式庫都必須向物件管理員註冊，才能提供符號流覽工具的符號。

 一般來說，您會在 VSPackage 載入時註冊程式庫。 不過，它可以視需要在另一個時間執行。 當 VSPackage 關閉時，您會取消註冊媒體櫃。

 若要註冊程式庫，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> 方法。 若為 managed 程式碼程式庫，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法。

 若要取消註冊程式庫，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> 方法。

 若要取得物件管理員的參考， <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 請將 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 服務識別碼傳遞給 `GetService` 方法。

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>使用物件管理員註冊和取消註冊程式庫

### <a name="to-register-a-library-with-the-object-manager"></a>若要使用物件管理員註冊程式庫

1. 建立程式庫。

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. 取得類型物件的參考 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> ，並呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法。

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>若要使用物件管理員取消註冊程式庫

1. 取得類型物件的參考 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> ，並呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> 方法。

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>另請參閱
- [舊版語言服務擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)
- [支援符號流覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [如何：將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
