Microsoft libraries needed for re-building CvGameCoreDLL.dll for Sid Meier's Civilization IV: Beyond the Sword (BtS). Might also work for Warlords and the Civ IV base game - this hasn't been tested.

1) Service Pack 1 of the 2003 Microsoft Visual C++ Toolkit
2) Version 6.0 of the Microsoft Windows Platform Software Development Kit

The community-created makefiles for BtS refer to these dependencies through variables named (usually) TOOLKIT and PSDK respectively. Each variable needs to be set to the path of the folder containing the bin, include and lib subfolders. As for the CIV4_PATH (or CIVINSTALL) variable - that one should point to the BtS install folder. Any other folder containing Boost 1.32 and Python 2.4 will also work. In any case, every modder and player should already have those two libraries, so I'm not including them here.

Regarding the specific library versions:
1) is based on this file attachment in the Caveman2Cosmos (C2C) subforum of CFC:
    https://forums.civfanatics.com/threads/caveman-2-cosmos-ideas-discussions-thread.377892/page-913#post-15499500
To reduce the download size, I've removed some lib files that BtS apparently doesn't use, as well as some source code and the included Windows Platform SDK. I've added
    msvcp71.dll (build 7.10.6030.0) and msvcr71.dll (build 7.10.6030.0)
from the download attached to the post preceding the one linked above, and
    dbghelp.dll (build 6.0.17.0)
from the installer recommended in Leoreth's thread:
    https://forums.civfanatics.com/threads/the-easiest-way-to-compile-a-new-dll.608137/
    https://sourceforge.net/projects/beyond-the-sword-sdk/
See this CFC post for context about these additions:
    https://forums.civfanatics.com/threads/cvgamecoredll-build-error-boost-python-list-hpp.648072/page-2#post-15515986

The main benefit of using SP 1 (from the C2C subforum) that I've encountered is that linking debug builds with msvcprtd no longer causes (misleading?) LNK4229 and LNK4078 warnings when std::stable_sort is used. At least one other (useful) std function seems to cause those warnings as well. And release builds with /OPT:REF no longer cause the LNK4089 warning.

2) has been obtained from this post in the C2C subforum:
    https://forums.civfanatics.com/threads/building-a-new-tag-in-c2c-code.640222/page-2#post-15449499
See this post for some more context:
    https://forums.civfanatics.com/threads/using-visual-studio-2019.645573/#post-15485531
There are at least two larger archives of (supposedly?) the same version floating around, namely:
    https://github.com/We-the-People-civ4col-mod/Compiler
    https://forums.civfanatics.com/threads/a-simple-guide-to-compiling-the-dll.405444/
And there's version 7.0A, which, I think, comes from the installer in Leoreth's thread:
    https://sourceforge.net/projects/beyond-the-sword-sdk/
That version might require Microsoft Visual Studio (VS) 2010, 2008 or 2005 to be installed alongside whichever version of VS or other IDE is used for editing the code and initiating the build process, and it might not work at all when using VS 2022. It may also be that v6.0 has all the same problems; see this CFC post for context:
https://forums.civfanatics.com/threads/modmodding-q-a-thread.516755/page-111#post-16257258
