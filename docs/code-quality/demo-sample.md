---
title: 用於程式碼分析的 C++ 專案範例
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 648d00cd59d056e0874c91338a39667088d93e2e
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018440"
---
# <a name="sample-c-project-for-code-analysis"></a>用於程式碼分析的 C++ 專案範例

下列程序會示範如何建立[逐步解說：分析 C/C++ 程式碼的缺失](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)範例。 這些程序會建立：

- 名為 CppDemo 的 Visual Studio 解決方案。

- 名為 CodeDefects 的靜態程式庫專案。

- 名為 Annotations 的靜態程式庫專案。

這些程序也會提供標頭的程式碼，以及用於靜態程式庫的 *.cpp* 檔案。

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>建立 CppDemo 解決方案和 CodeDefects 專案

1. 按一下 [檔案] 功能表，指向 [新增]，然後按一下 [新增專案]。

2. 在 [專案類型] 樹狀清單中，如果 Visual C++ 不是您的預設語言，請在 VS 中展開 [其他語言]。

3. 展開 [Visual C++]，然後按一下 [一般]。

4. 在 [範本] 中，按一下 [空白專案]。

5. 在 [名稱] 文字方塊中，鍵入 **CodeDefects**。

6. 選取 [為解決方案建立目錄] 核取方塊。

7. 在 [解決方案名稱] 文字方塊中，鍵入 **CppDemo**。

## <a name="configure-the-codedefects-project-as-a-static-library"></a>將 CodeDefects 專案設定為靜態程式庫

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [CodeDefects]，然後按一下 [屬性]。

2. 展開 [組態屬性]，然後按一下 [一般]。

3. 在 [一般] 清單中，選取 [目標副檔名] 旁邊資料行中的文字，然後鍵入 **.lib**。

4. 在 [專案預設] 中，按一下 [組態類型] 旁邊的資料行，然後按一下 [靜態程式庫 (.lib)]。

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>將標頭和來源檔案新增至 CodeDefects 專案

1. 在 [方案總管] 中，展開 [CodeDefects]，以滑鼠右鍵按一下 [標頭檔]，按一下 [新增]，然後按一下 [新增項目]。

2. 在 [新增項目] 對話方塊中，按一下 [程式碼]，然後按一下 [標頭檔 (.h)]。

3. 在 [名稱] 方塊中，鍵入 **Bug.h**，然後按一下 [新增]。

4. 複製下列程式碼，並將它貼入 Visual Studio 編輯器中的 *Bug.h* 檔案。

    ```cpp
    #include <windows.h>

    //
    //These 3 functions are consumed by the sample
    //  but are not defined. This project cannot be linked!
    //

    bool CheckDomain( LPCSTR );
    HRESULT ReadUserAccount();

    //
    //These constants define the common sizes of the
    //  user account information throughout the program
    //

    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

5. 在 [方案總管] 中，以滑鼠右鍵按一下 [來源檔案]，指向 [新增]，然後按一下 [新增項目]。

6. 在 [新增項目] 對話方塊中，按一下 [C++ 檔案 (.cpp)]

7. 在 [名稱] 方塊中，鍵入 **Bug.cpp**，然後按一下 [新增]。

8. 複製下列程式碼，並將它貼入 Visual Studio 編輯器中的 *Bug.cpp* 檔案。

    ```cpp
    #include <stdlib.h>
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount() )
        {

            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )
            {
                if ( g_userAccount[len] == '\\' )
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete [] domain;
                return false;
            }
            else
            {
                domain[len]='\0';
            }
            // Process domain string
            bool result = CheckDomain( domain );

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i+j;
    }
    ```

9. 按一下 [檔案] 功能表，然後按一下 [全部儲存]。

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>新增 Annotations 專案並將其設定為靜態程式庫

1. 在 [方案總管] 中，按一下 [CppDemo]，指向 [新增]，然後按一下 [新增專案]。

2. 在 [新增專案] 對話方塊中，展開 Visual C++，按一下 [一般]，然後按一下 [空白專案]。

3. 在 [名稱] 文字方塊中，鍵入 **Annotations**，然後按一下 [新增]。

4. 在 [方案總管] 中，以滑鼠右鍵按一下 [Annotations]，然後按一下 [屬性]。

5. 展開 [組態屬性]，然後按一下 [一般]。

6. 在 [一般] 清單中，選取 [目標副檔名] 旁邊資料行中的文字，然後鍵入 **.lib**。

7. 在 [專案預設] 中，按一下 [組態類型] 旁邊的資料行，然後按一下 [靜態程式庫 (.lib)]。

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>將標頭檔和來源檔案新增至 Annotations 專案

1. 在 [方案總管] 中，展開 [Annotations]，以滑鼠右鍵按一下 [標頭檔]，按一下 [新增]，然後按一下 [新增項目]。

2. 在 [新增項目] 對話方塊中，按一下 [標頭檔 (.h)]。

3. 在 [名稱] 方塊中，鍵入 **annotations.h**，然後按一下 [新增]。

4. 複製下列程式碼，並將它貼入 Visual Studio 編輯器中的 *annotations.h* 檔案。

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();

    ```

5. 在 [方案總管] 中，以滑鼠右鍵按一下 [來源檔案]，指向 [新增]，然後按一下 [新增項目]。

6. 在 [新增項目] 對話方塊中，按一下 [程式碼]，然後按一下 [C++ 檔案 (.cpp)]

7. 在 [名稱] 方塊中，鍵入 **annotations.cpp**，然後按一下 [新增]。

8. 複製下列程式碼，並將它貼入 Visual Studio 編輯器中的 *annotations.cpp* 檔案。

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>
    #include <windows.h>
    #include <stdlib.h>
    #include "annotations.h"

    LinkedList* AddTail( LinkedList *node, int value )
    {
        LinkedList *newNode = NULL;

        // finds the last node
        while ( node->next != NULL )
        {
            node = node->next;
        }

        // appends the new node
        newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }

    ```

9. 按一下 [檔案] 功能表，然後按一下 [全部儲存]。
