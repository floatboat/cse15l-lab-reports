# Lab Report 4, Week 8

[My markdown-parse repo (Thuan Do's)](https://github.com/floatboat/markdown-parse)

[Reviewed markdown-parse repo (Alexander Kourjanski's)](https://github.com/Alexander-Kourjanski/markdown-parse)

## Criteria of Passing Based on VScode preview

## Snippet 1

### Should produce:
```
[`google.com, google.com, ucsd.edu]]
```
### My Test Code:
```
    @Test
    public void testSnippet1() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-1.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("another link", "cod[e", "code]"), MarkdownParse.getLinks(regLines));
    }
```
### Reviewer Test Code:
```
    @Test
    public void testSnippet1() throws IOException {
        ArrayList<String> testfile2 = new ArrayList<>();
        testfile2.add("another link");
        testfile2.add("cod[e");
        testfile2.add("code]");
        String testfilemd = MarkdownParse.converter("./snippet-1.md");
        assertEquals(testfile2, MarkdownParse.getLinks(testfilemd));
    }
```
### My Output:
```
JUnit version 4.13.2
.....E
Time: 0.019
There was 1 failure:
1) testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[another link, cod[e, code]]> but was:<[url.com, `google.com, google.com, ucsd.edu]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:36)
```
### Reviewed Output:
```
1) testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[another link, cod[e, code]]> but was:<[url.com, `google.com, google.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:87)
```
### Answering Question #1:

I think that it will take more than a small code change to make my program work for snippet 1 and related cases using inline code with backticks. The reason I say this is because my program (mistakenly) tries to get links from parenthesis rather than within brackets. This results in bad output, so I would have to reinstate the brackets again. Also, my program hasn't accounted for backticks/other characters that could interfere with the brackets, so I would have to figure out something that would probably add more than 10 lines of code. 

## Snippet 2

### Should produce:
```
[nested link, a nested parenthesized url, some escaped [ brackets ]]
```
### My Test Code:
```
    @Test
    public void testSnippet2() throws IOException {
        String regFile = Files.readString(Path.of("./snippet-2.md"));
        String[] regLines = regFile.split("\n");
        assertEquals(List.of("nested link", "a nested parenthesized url", 
            "some escaped [ brackets ]"), MarkdownParse.getLinks(regLines));
    }
```
### Reviewer Test Code:
```

```
### My Output:
```
2) testSnippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[nested link, a nested parenthesized url, some escaped [ brackets ]]> but was:<[a.com, a.com((, example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet2(MarkdownParseTest.java:43)
```
### Reviewed Output:
```

```
### Answering Question #2:

## Snippet 3

### Should produce:
```

```
### My Test Code:
```

```
### Reviewer Test Code:
```

```
### My Output:
```

```
### Reviewed Output:
```

```
### Answering Question #3: