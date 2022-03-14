# separate_chinese_english
```
juzi='hello everyone 之前在微博 分享过一个英语句子I am because you are.然后有同学说这不是一个错句吗'

#=抽取中文其他部分都给英文

def _is_chinese_char(cp):
    """Checks whether CP is the codepoint of a CJK character."""
    # This defines a "chinese character" as anything in the CJK Unicode block:
    #   https://en.wikipedia.org/wiki/CJK_Unified_Ideographs_(Unicode_block)
    #
    # Note that the CJK Unicode block is NOT all Japanese and Korean characters,
    # despite its name. The modern Korean Hangul alphabet is a different block,
    # as is Japanese Hiragana and Katakana. Those alphabets are used to write
    # space-separated words, so they are not treated specially and handled
    # like the all of the other languages.
    if (
            (cp >= 0x4E00 and cp <= 0x9FFF)
            or (cp >= 0x3400 and cp <= 0x4DBF)  #
            or (cp >= 0x20000 and cp <= 0x2A6DF)  #
            or (cp >= 0x2A700 and cp <= 0x2B73F)  #
            or (cp >= 0x2B740 and cp <= 0x2B81F)  #
            or (cp >= 0x2B820 and cp <= 0x2CEAF)  #
            or (cp >= 0xF900 and cp <= 0xFAFF)
            or (cp >= 0x2F800 and cp <= 0x2FA1F)  #
    ):  #
        return True

    return False
chinese=''.join([i  if _is_chinese_char(ord(i)) else ' ' for i in juzi ])
english=''.join([i  if not _is_chinese_char(ord(i)) else ' ' for i in juzi ])
#首先我们进行中英文拆分.
#==================首先合成英文部分
a=chinese.split(' ')
b=english.split(' ')
flag=[] #中文标1,英文标0

for i in chinese:
    if i!=' ':
        flag.append(1)
    else:
        flag.append(0)
print(1)


#

#========算法思路就是每次取一个相同flag的片段, 然后把它变成wav信号.
start=0
end=0
out=[]
for i in range(1,len(flag)):
    if flag[i]!=flag[i-1] or i==len(flag)-1:
        out.append([juzi[start:i],flag[start]])
        # out.append([start,i,flag[start]])
        start=i
print(1)

```
