寫程式要寫註解！
寫程式不要寫註解！
OR
寫文章一定要寫註釋！
寫文章不要寫註釋！
  
寫程式要寫註解！
寫程式不要寫註解！
有沒有覺得很熟悉，有些人覺得寫程式不需要註解，有些人又覺得寫程式一定要寫註解！
  
我換個說法！！
  
寫文章一定要寫註釋！
寫文章不要寫註釋！
哈！有沒有覺得上面兩句話很有趣呢？
  
其實我覺得無論是要寫註解或不寫註解都沒有錯，端看這個程式碼的閱讀對象或這個程式碼的目的！如果是Sample Code給初學者，那你不寫註解恐怕會有一些人會看不懂！如果是Production code，只是需要做維護，那註解當然是越少越好阿！因為當時程很緊湊的時候，有些人改了程式碼之後，就是會忘了改註解！
  
<font color="Red">有時候錯誤的註解比沒有註解更令人覺得可怕！</font>
  
如果每個Method只有不到十行，那為何又要註解呢？（除了一些很特殊的程式碼之外，例如：正規劃表示式或…想不到了XD）
  
過時程式碼的註解
相信很多人一定會常常看到以下這個例子：
  
```c++
BOOL WriteData(InterfaceList *pIf, const BYTE buffer[], DWORD messageLog, OVERLAPPED *Overlap) {  
    ... (略)  
//  logMessage("Write (%d) %d bytes!\n", pIf->Index, messageLog);  
    pDev = &(pIf->hDev);  
/*  logMessage("write Data %d Bytes(%d)", messageLog, pIf->Index); 
    PrintMessageInHex((BYTE *) buffer, ((messageLog > MAX_LEN) ? MAX_ LEN : messageLog)); 
*/  
    ... (略)  
    if(result == FALSE) {  
        lastErrorCode = GetLastError();  
        if(lastErrorCode == ERROR_IO_PENDING) {  
//          logMessage("Send Pending!\n");  
            WaitForSingleObject(Overlap->hEvent, WRITE_MAX_WAIT);  
            GetOverlappedResult (*pDev, Overlap, &bytesForWritten, FALSE);  
//          logMessage("Sent Pending data!\n");  
        } else {  
            logMessage("DoWrite Error! (%d)\n", lastErrorCode);  
        }  
    }  
  
    ... (略)  
    return result;  
}  
```
  
通常這種情況在 Legacy code 是非常普遍的，可是不知道有沒有想過，既然都註解起來了為什麼要要留著呢？是要給後面維護的人參考嗎？還是要教後面的人這個API可能要這樣用呢？應該都不是吧！感覺有點像我女朋友常常念我的一句話：『你（說我）怎麼這麼愛蒐集垃圾阿！』當然，我蒐集的鐵定不是垃圾，而是將來可能會用到的物品（突然覺得好心虛）。
  
通常作家在寫作時我相信也一定會修修改改的，但是我更相信，他們（作家）絕對不會把修改掉的內容在放在書本裡！因為好像沒什麼意義，除非那是一本交我們怎麼修改文章的書籍。
  
所以結論是：通常需要註解的程式碼，有很高的機率都可以改寫成不需要註解的。