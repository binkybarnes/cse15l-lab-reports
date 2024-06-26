# Lab Report 3

## Part 1 - Bugs

### bug in ArrayExamples.java

1.

```
assertEquals(2.0, ArrayExamples.averageWithoutLowest(new double[]{1.0, 1.0, 2.0, 3.0}), .001);

static double averageWithoutLowest(double[] arr) {
  if(arr.length < 2) { return 0.0; }
  double lowest = arr[0];
  for(double num: arr) {
    if(num < lowest) { lowest = num; }
  }
  double sum = 0;
  for(double num: arr) {
    if(num != lowest) { sum += num; }
  }
  return sum / (arr.length - 1);
}
```

2.

```
assertEquals(3.5, ArrayExamples.averageWithoutLowest(new double[] { 2.0, 3.0, 4.0 }), 0.001);

static double averageWithoutLowest(double[] arr) {
  if(arr.length < 2) { return 0.0; }
  double lowest = arr[0];
  for(double num: arr) {
    if(num < lowest) { lowest = num; }
  }
  double sum = 0;
  for(double num: arr) {
    if(num != lowest) { sum += num; }
  }
  return sum / (arr.length - 1);
}
```

3.

```
%TESTC  1 v2
%TSTTREE1,test1(lab3Report),false,1,false,-1,test1(lab3Report),,
%TESTS  1,test1(lab3Report)
%FAILED 1,test1(lab3Report)
%TRACES
java.lang.AssertionError: expected:<2.0> but was:<1.6666666666666667>
%TRACEE
%TESTE  1,test1(lab3Report)
%RUNTIME9
```

```
%TESTC  1 v2
%TSTTREE1,test2(lab3Report),false,1,false,-1,test2(lab3Report),,
%TESTS  1,test2(lab3Report)
%TESTE  1,test2(lab3Report)
%RUNTIME7
```

4.  Before

```
static double averageWithoutLowest(double[] arr) {
  if (arr.length < 2) {
    return 0.0;
  }
  double lowest = arr[0];
  for (double num : arr) {
    if (num < lowest) {
      lowest = num;
    }
  }
  double sum = 0;
  for (double num : arr) {
    if (num != lowest) {
      sum += num;
    }
  }
  return sum / (arr.length - 1);
}
```

After

```
static double averageWithoutLowest(double[] arr) {
  if (arr.length < 2) {
    return 0.0;
  }
  double lowest = arr[0];
  for (double num : arr) {
    if (num < lowest) {
      lowest = num;
    }
  }
  double sum = 0;
  booelean flag = false;
  for (double num : arr) {
    if (flag == false && num == lowest) {
        flag = true;
        continue;
    }
      sum += num;
  }
  return sum / (arr.length - 1);
}
```

5.  The problem with the original code is that it removes all occurrences of the smallest number, but only subtracts 1 from the total number when taking the average.

I fixed it by removing only one occurrence of the smallest number. Unless the intended design is that all occurrences are to be removed, then I would have to subtract the number of numbers removed that were removed from the total.

---

## Part 2 - Researching commands

### 4 grep options

1. `grep -r`: search recursively. It is useful for searching in all text files that are nested within directories.

   i. source: https://www.gnu.org/software/grep/manual/grep.html

   a. ex: `grep -r "monkeys is"` It is finding the occurrences of "monkeys is" in each file in the nested directories.

   ```
   > grep -r "monkeys is"
   ./biomed/1471-2210-1-7.txt:        rats, mice and monkeys is well documented (for review see
   ```

   b. ex: `grep -r "among us"` This finds all occurrences of among us within each nested directory.

   ```
   > grep -r "among us"
   ./government/Post_Rate_Comm/ReportToCongress2002WEB.
   txt:unreasonable discrimination among users of the mails, nor shall it
   ./biomed/1471-2261-3-5.txt:        clinically diagnosed valve disease among users of
   ```

2. `grep -i`: ignore case. This is useful if you do not care about whether a pattern is capitalized or not. This provide a broader search for what you are looking for.

   i. source: https://www.gnu.org/software/grep/manual/grep.html

   a. ex: `grep -i "MIlwaukeE"` This finds all occurrences of milwaukee whether or not any of the leters are cpaitalized or not.

   ```
   > grep -i "MIlwaukeE"
   ./government/About_LSC/Strategic_report.txt:(Milwaukee)
   ./government/About_LSC/Strategic_report.txt:NLADA Annual Conference in Milwaukee to showcase best practices in
   ./plos/pmed.0010066.txt:          MRI was performed at 1.5 T
   (System 9X, General Electric Medical Systems, Milwaukee,
   ./biomed/1471-2180-2-22.txt:          (Milwaukee, WI).
   Nicotinamide-adenine dinucleotide (NAD),
   ./biomed/1471-2172-3-1.txt:          were purchased from Fluka (Milwaukee, Wl). Nylon Hybond
   ./biomed/1471-2490-3-2.txt:        Electrical medical systems, Milwaukee, WI). The exposure
   ./biomed/1471-2210-2-4.txt:          purchased from Aldrich Chemical Co., Milwaukee, WI.
   ./biomed/1471-2121-3-21.txt:          2 ) was from Aldrich (Milwaukee, WI).
   ```

   b. ex: `grep -i "RIZz"` This finds all occurrences of the substring rizz in any file regardless of case.

   ```
   > grep -i "RIZz"
   ./government/Media/pro_bono_efforts.txt:By Russ Rizzo
   ./biomed/ar331.txt:        51]. Zhao and colleagues [ 52] identified frizzled (denoted
   ./biomed/ar331.txt:        Of potential importance is the fact that frizzled family
   ./biomed/ar331.txt:        colleagues in rheumatoid arthritis [ 53]. A new frizzled
   ./biomed/ar331.txt:        54]. Perhaps down-regulation of frizzled family members by
   ./biomed/1471-213X-2-7.txt:        frizzled (
   ./biomed/1471-213X-2-7.txt:        frizzled pathway regulates the
   ...
   ```

3. `grep -w`: search for whole word, not substring. This is useful when you want to search for the exact word insated of having it a part of a substring.

   i. source: https://www.gnu.org/software/grep/manual/grep.html

   a. ex: `grep -w "cysteine protease"` finds the two words together cystein protease.

   ```
   > grep -w "cysteine protease"
   ./plos/journal.pbio.0020013.txt:        for the proteasome, in
   addition to “classic” cysteine protease behavior
   (Verma et al. 2002;
   ./biomed/1476-4598-2-25.txt:          Cathepsin B is a lysosomal cysteine protease, the
   ./biomed/1476-4598-2-25.txt:          cysteine protease. The cleavage of calpastatin by
   ./biomed/1471-2180-1-33.txt:          cysteine protease, SpeB [ 4 ] . Analysis of SpeB, SK and
   ./biomed/1471-2180-1-33.txt:        restored; however secretion of the cysteine protease, SpeB,
   ./biomed/1471-2180-1-33.txt:          405 over time. The cysteine protease
   ./biomed/1471-2180-1-33.txt:          the presence of a cysteine protease.
   ./biomed/gb-2002-3-12-research0077.txt:          cysteine protease [ 36]. JEvTrace also serves as a
   ./biomed/gb-2003-4-2-r9.txt:            these include a cysteine protease, falcipain-2
   ```

   b. ex: `grep -w "explode"` Finds the exact match for the word explode.

   ```
   > grep -w "explode"
   ./biomed/cc2190.txt:          enteral nutrition (explode) AND jejunal or post-pyloric
   ./911report/chapter-6.txt:
   hit tanks, not people. It needed to be designed to explode in
   a different way, and
   ```

4. `grep -l`: display file names which contain line matches. This is useful when you want to find the files that include the information that you want.

   i. source: https://www.gnu.org/software/grep/manual/grep.html

   a. ex: `grep -l "toilet"` This finds all the files that contain toilet. These names of the files can be used for further processing.

   ```
   > grep -l "toilet"
   ./government/Media/Farm_workers.txt
   ./government/Media/Bridging_legal_aid_gap.txt
   ./biomed/1471-2458-3-2.txt
   ./biomed/1472-684X-1-5.txt
   ./911report/chapter-5.txt
   ./911report/chapter-6.txt
   ```

   b. ex: `grep -l "killed.*air strike"` This finds the pattern of killed air strike and returns the names of all the files that contain this pattern.

   ```
   > grep -l "killed.*air strike"
   ./911report/chapter-10.txt
   ```
