---
title: "如何: 識別文件庫中的符號 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "呼叫瀏覽器工具，用來識別文件庫中的符號"
  - "呼叫瀏覽器工具"
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 如何: 識別文件庫中的符號
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

符號瀏覽工具會顯示符號的階層式檢視。  符號代表命名空間、 物件、 類別、 類別成員和其他語言項目。  
  
 在階層中的每個符號可以由傳至符號集瀏覽資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員，透過下列介面：  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 階層架構中符號的位置來區別符號。  它可讓瀏覽至特定符號的符號瀏覽工具。  唯一且完整的路徑，該符號的位置來決定的。  在路徑中的每個項目是一個節點。  路徑開頭為最上層的節點，並結束該特定的符號。  比方說，如果 M1 方法 C1 類別的成員則 C1 是 N1 命名空間中，M1 方法的完整路徑是 N1。C1。M1。  此路徑包含三個節點： N1，C1，和 M1。  
  
 瀏覽資訊可以讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員來找出，請選取階層架構中的符號。  它可讓兩個瀏覽工具巡覽到另一個。  在使用時**物件瀏覽器**來瀏覽中的符號[!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]專案，方法上按一下滑鼠右鍵，並開始**呼叫瀏覽器**工具，以顯示呼叫圖形中的方法。  
  
 兩種形式描述符號位置。  標準的格式根據符號的完整路徑。  它所代表的符號階層架構中唯一的位置。  很獨立於符號瀏覽\] 工具。  若要取得標準格式的資訊， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>方法。  展示表單將告訴您在特定的符號瀏覽工具中符號的位置。  符號的位置是相對於其他符號在 hierarchicy 中的位置。  指定的符號可能會有數個簡報的路徑，但只有一個標準的路徑。  例如，假設 C1 類別從 C2 類別繼承，而這兩個類別是 N1 命名空間中**物件瀏覽器**會顯示以下的階層式樹狀目錄：  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 C2 類別，在這個範例中，標準路徑是 N1 \+ C2。  C2 的簡報路徑包括 C1 與 「 基底和介面 」 的節點： N1 \+ C1 \+"基底和介面"\+ C2。  
  
 若要取得簡報表單資訊的物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>方法。  
  
## 用來識別的階層架構中的符號  
  
#### 若要取得正式而且簡報表單資訊  
  
1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 方法。  
  
     物件管理員會呼叫這個方法，以取得正式的符號路徑中所含的節點清單。  
  
    ```vb#  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```c#  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 方法。  
  
     物件管理員會呼叫這個方法，以取得該符號的簡報路徑中所含的節點清單。  
  
## 請參閱  
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [如何: 使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何: 公開 \(expose\) 的程式庫物件管理員提供的符號清單](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)