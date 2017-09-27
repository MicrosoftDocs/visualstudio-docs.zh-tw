---
title: "公開的物件管理員來提供的符號清單 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsSimpleLibrary2 interface, lists of symbols
- IVsLibrary2 interface, lists of symbols
- symbols, call browser
- lists, symbols for the object manager
- symbols, exposing lists to the object manager
ms.assetid: 19757068-bdaa-4e7e-85d6-f8ce5026a859
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 502fbce9d9fbd187e0cccb0b613d470a23f09e10
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager"></a>如何： 公開清單的程式庫提供對物件管理員中的符號
符號瀏覽工具，**類別檢視**，**物件瀏覽器**，**呼叫瀏覽器**和**尋找符號結果**，傳遞至新資料的要求[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員。 物件管理員尋找適當的程式庫，並要求新的符號清單。 藉由提供要求的資料，以回應文件庫[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員呼叫方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面來取得資料，並使用它來擴展或更新符號瀏覽工具的檢視。  
  
 此工具會叫用、 展開節點，或重新整理檢視時，程式庫可能會收到資料的要求。 第一次叫用的符號瀏覽工具時，物件管理員要求的程式庫，以提供最上層的清單。 當使用者展開清單節點時，程式庫會提供該節點下的子系清單。 每個物件管理員查詢包含感興趣項目的索引。 若要顯示新的清單，物件管理員必須決定多少項目在清單中，項目，其名稱、 存取範圍，以及其他屬性的類型。  
  
> [!NOTE]
>  下列的 managed 程式碼範例示範如何提供的符號，透過實作清單<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。 物件管理員這個介面中呼叫的方法，並使用取得的資料填入或更新的符號瀏覽工具。  
>   
>  如需原生程式碼的符號提供者實作，使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>介面。  
  
## <a name="providing-lists-of-symbols-to-the-object-manager"></a>提供對物件管理員中的符號清單  
  
#### <a name="to-provide-lists-of-symbols-to-the-object-manager"></a>物件管理員提供的符號清單  
  
1.  取得的符號清單中的項目數目，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>方法。 下列範例會示範如何 object manager 取得資訊清單中的項目數。  
  
    ```vb  
    Protected m_Methods As System.Collections.Generic.SortedList(Of String, Method) = New System.Collections.Generic.SortedList(Of String, Method)()  
  
    Public Function GetItemCount(ByRef pCount As UInteger) As Integer  
        pCount = CUInt(m_Methods.Count)  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    protected System.Collections.Generic.SortedList<string, Method> m_Methods = new System.Collections.Generic.SortedList<string, Method>();  
  
    public int GetItemCount(out uint pCount)  
    {  
        pCount = (uint)m_Methods.Count;  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
2.  取得資訊的類別，以及指定的清單項目的屬性，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>方法。 中指定的項目分類<xref:Microsoft.VisualStudio.Shell.Interop.LIB_CATEGORY>列舉型別。 下列範例會示範如何物件管理員取得的項目指定類別的屬性。  
  
    ```vb  
    Public Function GetCategoryField2(ByVal index As UInteger, ByVal Category As Integer, ByRef pfCatField As UInteger) As Integer  
        pfCatField = 0  
  
        Select Case CType(Category, LIB_CATEGORY)  
            Case LIB_CATEGORY.LC_MEMBERTYPE  
                pfCatField = CUInt(_LIBCAT_MEMBERTYPE.LCMT_METHOD)  
  
            Case LIB_CATEGORY.LC_MEMBERACCESS  
                Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
  
                If method.IsPublic Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PUBLIC)  
                ElseIf method.IsPrivate Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PRIVATE)  
                ElseIf method.IsFamily Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED)  
                ElseIf method.IsFamilyOrAssembly Then  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED) Or CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)  
                Else  
                    ' Show everything else as internal.  
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)  
                End If  
  
            Case LIB_CATEGORY.LC_VISIBILITY  
                pfCatField = CUInt(_LIBCAT_VISIBILITY.LCV_VISIBLE)  
  
            Case LIB_CATEGORY.LC_LISTTYPE  
                pfCatField = CUInt(_LIB_LISTTYPE.LLT_MEMBERS)  
  
            Case Else  
                Return Microsoft.VisualStudio.VSConstants.S_FALSE  
        End Select  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int GetCategoryField2(uint index, int Category, out uint pfCatField)  
    {  
        pfCatField = 0;  
  
        switch ((LIB_CATEGORY)Category)  
        {  
            case LIB_CATEGORY.LC_MEMBERTYPE:  
                pfCatField = (uint)_LIBCAT_MEMBERTYPE.LCMT_METHOD;  
                break;  
  
            case LIB_CATEGORY.LC_MEMBERACCESS:  
                {  
                    Method method = m_Methods.Values[(int)index];  
  
                    if (method.IsPublic)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PUBLIC;  
                    }  
                    else if (method.IsPrivate)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PRIVATE;  
                    }  
                    else if (method.IsFamily)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED;  
                    }  
                    else if (method.IsFamilyOrAssembly)  
                    {  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED |  
                                     (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;  
                    }  
                    else  
                    {  
                        // Show everything else as internal.  
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;  
                    }  
                }  
                break;  
  
            case LIB_CATEGORY.LC_VISIBILITY:  
                pfCatField = (uint)_LIBCAT_VISIBILITY.LCV_VISIBLE;  
                break;  
  
            case LIB_CATEGORY.LC_LISTTYPE:  
                pfCatField = (uint)_LIB_LISTTYPE.LLT_MEMBERS;  
                break;  
  
            default:  
                return Microsoft.VisualStudio.VSConstants.S_FALSE;  
        }  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
3.  取得指定的清單項目的文字表示，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>方法。 下列範例示範如何取得指定項目的完整名稱。  
  
    ```vb  
    Public Function GetTextWithOwnership(<System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")> ByVal index As UInteger, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")> ByVal tto As Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")> ByRef ppszText As String) As Integer  
        ppszText = m_Methods.Values(CInt(Fix(index))).FullName  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int GetTextWithOwnership([System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")] uint index, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")] Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS tto, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")] out string ppszText)  
    {  
        ppszText = m_Methods.Values[(int)index].FullName;  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
4.  取得指定的清單項目的圖示資訊藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>方法。 圖示代表的類型 （類別、 方法等等） 和存取範圍 （私人、 公用，等等） 的清單項目。 下列範例示範如何取得根據指定的項目屬性的圖示資訊。  
  
    ```vb  
    Public Overridable Function GetDisplayData(ByVal index As UInteger, ByVal pData As Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA()) As Integer  
        If pData Is Nothing Then  
            Return Microsoft.VisualStudio.VSConstants.E_INVALIDARG  
        End If  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
  
        Dim iImage As Integer = 12 * 6 ' See env\inc\OMGlyphs.h.  
  
        Const OM_GLYPH_ACC_PUBLIC As Integer = 0  
        Const OM_GLYPH_ACC_INTERNAL As Integer = 1  
        Const OM_GLYPH_ACC_PROTECTED As Integer = 3  
        Const OM_GLYPH_ACC_PRIVATE As Integer = 4  
  
        If method.IsPublic Then  
            iImage += OM_GLYPH_ACC_PUBLIC  
        ElseIf method.IsPrivate Then  
            iImage += OM_GLYPH_ACC_PRIVATE  
        ElseIf method.IsFamily Then  
            iImage += OM_GLYPH_ACC_PROTECTED  
        ElseIf method.IsFamilyOrAssembly Then  
            iImage += OM_GLYPH_ACC_PROTECTED  
        Else  
            iImage += OM_GLYPH_ACC_INTERNAL  
        End If  
  
        pData(0).Image = CUShort(iImage)  
        pData(0).SelectedImage = CUShort(iImage)  
  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public virtual int GetDisplayData(uint index, Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA[] pData)  
    {  
        if (pData == null)  
        {  
            return Microsoft.VisualStudio.VSConstants.E_INVALIDARG;  
        }  
  
        Method method = m_Methods.Values[(int)index];  
  
        int iImage = 12 * 6;    // See env\inc\OMGlyphs.h.  
  
        const int OM_GLYPH_ACC_PUBLIC = 0;  
        const int OM_GLYPH_ACC_INTERNAL = 1;  
        const int OM_GLYPH_ACC_PROTECTED = 3;  
        const int OM_GLYPH_ACC_PRIVATE = 4;  
  
        if (method.IsPublic)  
        {  
            iImage += OM_GLYPH_ACC_PUBLIC;  
        }  
        else if (method.IsPrivate)  
        {  
            iImage += OM_GLYPH_ACC_PRIVATE;  
        }  
        else if (method.IsFamily)  
        {  
            iImage += OM_GLYPH_ACC_PROTECTED;  
        }  
        else if (method.IsFamilyOrAssembly)  
        {  
            iImage += OM_GLYPH_ACC_PROTECTED;  
        }  
        else  
        {  
            iImage += OM_GLYPH_ACC_INTERNAL;  
        }  
  
        pData[0].Image = (ushort)iImage;  
        pData[0].SelectedImage = (ushort)iImage;  
  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    ```  
  
5.  取得有關指定的清單項目是否可展開藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>方法。 下列範例會示範如何取得在指定的項目是否可以展開的資訊。  
  
    ```vb  
    Public Function GetExpandable(ByVal index As UInteger, ByRef pfExpandable As Integer) As Integer  
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
  
    Public Function GetExpandable3(ByVal index As UInteger, ByVal ListTypeExcluded As UInteger, ByRef pfExpandable As Integer) As Integer  
        Return GetExpandable(index, pfExpandable)  
    End Function  
    ```  
  
    ```csharp  
    public int GetExpandable(uint index, out int pfExpandable)  
    {  
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE;  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    public int GetExpandable3(uint index, uint ListTypeExcluded, out int pfExpandable)  
    {  
        return GetExpandable(index, out pfExpandable);  
    }  
  
    ```  
  
6.  藉由實作取得子系清單的指定的清單項目符號<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>方法。 下列範例示範如何取得子系清單的指定項目符號**呼叫**或**呼叫端**圖形。  
  
    ```vb  
    ' Call graph list.  
    Public Class CallsList  
        Inherits ResultsList  
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
        Public Sub New(ByVal library As Library)  
            MyBase.New(library)  
        End Sub  
  
        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
            Return MyBase.GetCallsList(index, ppList)  
        End Function  
    End Class  
  
    ' Callers graph list.  
    Public Class CallersList  
        Inherits ResultsList  
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
        Public Sub New(ByVal library As Library)  
            MyBase.New(library)  
        End Sub  
  
        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
            Return MyBase.GetCallersList(index, ppList)  
        End Function  
    End Class  
  
    ' Call graph list.  
    Public Function GetCallsList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
        ppList = Nothing  
        Dim callsList As ResultsList = New CallsList(m_Library)  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
        Dim strMethod As String = method.m_strPrototype  
  
        Dim Calls As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallGraph(method)  
  
        For i As Integer = 0 To Calls.Count - 1  
            Dim caller As Method = Calls(i).m_Target  
            callsList.AddMethod(caller)  
        Next i  
  
        ppList = CType(callsList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
  
    ' Callers graph list.  
    Public Function GetCallersList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
        ppList = Nothing  
        Dim callersList As ResultsList = New CallersList(m_Library)  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
        Dim strMethod As String = method.m_strPrototype  
  
        Dim Callers As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallersGraph(method)  
  
        For i As Integer = 0 To Callers.Count - 1  
            Dim caller As Method = Callers(i).m_Source  
            callersList.AddMethod(caller)  
        Next i  
  
        ppList = CType(callersList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)  
        Return Microsoft.VisualStudio.VSConstants.S_OK  
    End Function  
  
    ' Get a child list of symbols for a given list item.  
    Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer  
        ppList = Nothing  
  
        Dim method As Method = m_Methods.Values(CInt(Fix(index)))  
        Dim strMethod As String = method.m_strPrototype  
  
        ' Determine if the list belongs to Call or Callers graphs.  
        If CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM)) > 0 Then  
            ' Build the list for the Call graph.  
            Return MyBase.GetCallsList(index, ppList)  
        ElseIf CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO)) > 0 Then  
            ' Build the list for the Callers graph.  
            Return MyBase.GetCallersList(index, ppList)  
        End If  
  
        Return Microsoft.VisualStudio.VSConstants.E_FAIL  
    End Function  
    ```  
  
    ```csharp  
    // Call graph list.  
    public class CallsList :  
        ResultsList,  
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
    {  
        public CallsList(Library library) :  
            base(library)  
        {  
        }  
  
        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
        {  
            return base.GetCallsList(index, out ppList);  
        }  
    }  
  
    // Callers graph list.  
    public class CallersList :  
        ResultsList,  
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2  
    {  
        public CallersList(Library library) :  
            base(library)  
        {  
        }  
  
        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
        {  
            return base.GetCallersList(index, out ppList);  
        }  
    }  
  
    // Call graph list.  
    public int GetCallsList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
    {  
        ppList = null;  
        ResultsList callsList = new CallsList(m_Library);  
  
        Method method = m_Methods.Values[(int)index];  
        string strMethod = method.m_strPrototype;  
  
        System.Collections.Generic.List<CallInstance> Calls = m_Library.CallGraph.GetCallGraph(method);  
  
        for (int i = 0; i < Calls.Count; i++)  
        {  
            Method caller = Calls[i].m_Target;  
            callsList.AddMethod(caller);  
        }  
  
        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callsList);  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    // Callers graph list.  
    public int GetCallersList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
    {  
        ppList = null;  
        ResultsList callersList = new CallersList(m_Library);  
  
        Method method = m_Methods.Values[(int)index];  
        string strMethod = method.m_strPrototype;  
  
        System.Collections.Generic.List<CallInstance> Callers = m_Library.CallGraph.GetCallersGraph(method);  
  
        for (int i = 0; i < Callers.Count; i++)  
        {  
            Method caller = Callers[i].m_Source;  
            callersList.AddMethod(caller);  
        }  
  
        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callersList);  
        return Microsoft.VisualStudio.VSConstants.S_OK;  
    }  
  
    // Get a child list of symbols for a given list item.  
    public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)  
    {  
        ppList = null;  
  
        Method method = m_Methods.Values[(int)index];  
        string strMethod = method.m_strPrototype;  
  
        // Determine if the list belongs to Call or Callers graphs.  
        if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM) > 0)  
        {  
            // Build the list for the Call graph.  
            return base.GetCallsList(index, out ppList);  
        }  
        else if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO) > 0)  
        {  
            // Build the list for the Callers graph.  
            return base.GetCallersList(index, out ppList);  
        }  
  
        return Microsoft.VisualStudio.VSConstants.E_FAIL;  
    }  
  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [支援的符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [如何： 註冊物件管理員與程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何： 識別文件庫中的符號](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)   
 [舊版語言服務的擴充性](../../extensibility/internals/legacy-language-service-extensibility.md)
