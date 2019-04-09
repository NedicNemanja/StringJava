# StringJava

<p>A parser and translator for a language supporting string operations.. The language supports the concatenation operator over strings, function definitions and calls, conditionals (if-else i.e, every "if" must be followed by an "else"), and the following logical expressions:</p>
<ul>
<li>is-prefix-of (string1 prefix string2): Whether string1 is a prefix of string2.</li>
<li>is-suffix-of (string1 suffix string2): Whether string1 is a suffix of string2.</li>
</ul>
<p>All values in the language are string .</p>
<p>The parser, based on a context-free grammar, will translate the input language into Java. With the will use JavaCUP for the generation of the parser combined with JFlex lexer.</p>
<p>Infr the desired syntax of the input and output languages from the examples below. The output language is a subset of Java so it can be compiled using the "javac" command and executed using the "java" command or online Java compilers like <a href="http://repl.it/languages/java">this</a>, if you want to test your output.</p>
<p>There is no need to perform type checking for the argument types or a check for the number of function arguments. You can assume that the program input will always be semantically correct.</p>
<p>Note that each file of Java source code you produce must have the same name as the public Java class in it. For your own convenience you can name the public class &quot;Main&quot; and the generated files &quot;Main.java&quot;. In order to compile a file named Main.java you need to execute the command: javac Main.java. In order to execute the produced Main.class file you need to execute: java Main.</p>
<p>To execute the program successfully, the &quot;Main&quot; class of your Java program must have a method with the following signature: public static void main(String[] args), which will be the main method of your program, containing all the translated statements of the input program. Moreover, for each function declaration of the input program, the translated Java program must contain an equivalent static method of the same name. Finaly, keep in mind that in the input language the function declations must precede all statements.</p>
<h3 id="example-1">Example #1</h3>
<p><strong>Input:</strong></p>

<!--Created using tohtml.com -->
<pre style="color:#000000;background:#ffffff;">    name<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span>  <span style="color:#800080; ">{</span>
        <span style="color:#800000; ">"</span><span style="color:#0000e6; ">John</span><span style="color:#800000; ">"</span>
    <span style="color:#800080; ">}</span>
    
    surname<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span> <span style="color:#800080; ">{</span>
        <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Doe</span><span style="color:#800000; ">"</span>
    <span style="color:#800080; ">}</span>
    
    fullname<span style="color:#808030; ">(</span>first_name<span style="color:#808030; ">,</span> sep<span style="color:#808030; ">,</span> last_name<span style="color:#808030; ">)</span> <span style="color:#800080; ">{</span>
        first_name <span style="color:#808030; ">+</span> sep <span style="color:#808030; ">+</span> last_name
    <span style="color:#800080; ">}</span>

    name<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span>
    surname<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span>
    fullname<span style="color:#808030; ">(</span>name<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span><span style="color:#808030; ">,</span> <span style="color:#800000; ">"</span><span style="color:#0000e6; "> </span><span style="color:#800000; ">"</span><span style="color:#808030; ">,</span> surname<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span><span style="color:#808030; ">)</span>
</pre>


<p><strong>Output (Java):</strong></p>
<pre style='color:#000000;background:#ffffff;'>public class Main <span style='color:#800080; '>{</span>
    public <span style='color:#800000; font-weight:bold; '>static</span> <span style='color:#800000; font-weight:bold; '>void</span> <span style='color:#400000; '>main</span><span style='color:#808030; '>(</span><span style='color:#603000; '>String</span><span style='color:#808030; '>[</span><span style='color:#808030; '>]</span> args<span style='color:#808030; '>)</span> <span style='color:#800080; '>{</span>
        System<span style='color:#808030; '>.</span>out<span style='color:#808030; '>.</span>println<span style='color:#808030; '>(</span>name<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#808030; '>)</span><span style='color:#800080; '>;</span>
        System<span style='color:#808030; '>.</span>out<span style='color:#808030; '>.</span>println<span style='color:#808030; '>(</span>surname<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#808030; '>)</span><span style='color:#800080; '>;</span>
        System<span style='color:#808030; '>.</span>out<span style='color:#808030; '>.</span>println<span style='color:#808030; '>(</span>fullname<span style='color:#808030; '>(</span>name<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#808030; '>,</span> <span style='color:#800000; '>"</span><span style='color:#0000e6; '> </span><span style='color:#800000; '>"</span><span style='color:#808030; '>,</span> surname<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span><span style='color:#808030; '>)</span><span style='color:#808030; '>)</span><span style='color:#800080; '>;</span>
    <span style='color:#800080; '>}</span>

    public <span style='color:#800000; font-weight:bold; '>static</span> <span style='color:#603000; '>String</span> name<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span> <span style='color:#800080; '>{</span>
        <span style='color:#800000; font-weight:bold; '>return</span> <span style='color:#800000; '>"</span><span style='color:#0000e6; '>John</span><span style='color:#800000; '>"</span><span style='color:#800080; '>;</span>
    <span style='color:#800080; '>}</span>

    public <span style='color:#800000; font-weight:bold; '>static</span> <span style='color:#603000; '>String</span> surname<span style='color:#808030; '>(</span><span style='color:#808030; '>)</span> <span style='color:#800080; '>{</span>
        <span style='color:#800000; font-weight:bold; '>return</span> <span style='color:#800000; '>"</span><span style='color:#0000e6; '>Doe</span><span style='color:#800000; '>"</span><span style='color:#800080; '>;</span>
    <span style='color:#800080; '>}</span>

    public <span style='color:#800000; font-weight:bold; '>static</span> <span style='color:#603000; '>String</span> fullname<span style='color:#808030; '>(</span><span style='color:#603000; '>String</span> firstname<span style='color:#808030; '>,</span> <span style='color:#603000; '>String</span> sep<span style='color:#808030; '>,</span> <span style='color:#603000; '>String</span> last_name<span style='color:#808030; '>)</span> <span style='color:#800080; '>{</span>
        <span style='color:#800000; font-weight:bold; '>return</span> <span style='color:#800000; '>first_name + sep + last_name;</span>
    <span style='color:#800080; '>}</span>
<span style='color:#800080; '>}</span>
</pre>
<h3 id="example-2">Example #2</h3>
<p><strong>Input:</strong></p>


<pre style="color:#000000;background:#ffffff;">    name<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span> <span style="color:#800080; ">{</span>
        <span style="color:#800000; ">"</span><span style="color:#0000e6; ">John</span><span style="color:#800000; ">"</span>
    <span style="color:#800080; ">}</span>

    repeat<span style="color:#808030; ">(</span>x<span style="color:#808030; ">)</span> <span style="color:#800080; ">{</span>
        x <span style="color:#808030; ">+</span> x
    <span style="color:#800080; ">}</span>

    cond_repeat<span style="color:#808030; ">(</span>c<span style="color:#808030; ">,</span> x<span style="color:#808030; ">)</span> <span style="color:#800080; ">{</span>
        <span style="color:#800000; font-weight:bold; ">if</span> <span style="color:#808030; ">(</span>c prefix <span style="color:#800000; ">"</span><span style="color:#0000e6; ">yes</span><span style="color:#800000; ">"</span><span style="color:#808030; ">)</span>
            <span style="color:#800000; font-weight:bold; ">if</span><span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">yes</span><span style="color:#800000; ">"</span> prefix c<span style="color:#808030; ">)</span>
                repeat<span style="color:#808030; ">(</span>x<span style="color:#808030; ">)</span>
            <span style="color:#800000; font-weight:bold; ">else</span>
                x
        <span style="color:#800000; font-weight:bold; ">else</span>
            x
    <span style="color:#800080; ">}</span>

    cond_repeat<span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">yes</span><span style="color:#800000; ">"</span><span style="color:#808030; ">,</span> name<span style="color:#808030; ">(</span><span style="color:#808030; ">)</span><span style="color:#808030; ">)</span>
    cond_repeat<span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">no</span><span style="color:#800000; ">"</span><span style="color:#808030; ">,</span> <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Jane</span><span style="color:#800000; ">"</span><span style="color:#808030; ">)</span>
</pre>

<h3 id="example-3">Example #3</h3>
<p><strong>Input:</strong></p>


<pre style="color:#000000;background:#ffffff;">    findLangType<span style="color:#808030; ">(</span>langName<span style="color:#808030; ">)</span> <span style="color:#800080; ">{</span>
        <span style="color:#800000; font-weight:bold; ">if</span> <span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">Java</span><span style="color:#800000; ">"</span> prefix langName<span style="color:#808030; ">)</span>
            <span style="color:#800000; font-weight:bold; ">if</span><span style="color:#808030; ">(</span>langName prefix <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Java</span><span style="color:#800000; ">"</span><span style="color:#808030; ">)</span>
                <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Static</span><span style="color:#800000; ">"</span>
            <span style="color:#800000; font-weight:bold; ">else</span>
                <span style="color:#800000; font-weight:bold; ">if</span><span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">script</span><span style="color:#800000; ">"</span> suffix langName<span style="color:#808030; ">)</span>
                    <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Dynamic</span><span style="color:#800000; ">"</span>
                <span style="color:#800000; font-weight:bold; ">else</span>
                    <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Unknown</span><span style="color:#800000; ">"</span>
        <span style="color:#800000; font-weight:bold; ">else</span>
            <span style="color:#800000; font-weight:bold; ">if</span> <span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">script</span><span style="color:#800000; ">"</span> suffix langName<span style="color:#808030; ">)</span>
                <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Probably Dynamic</span><span style="color:#800000; ">"</span>
            <span style="color:#800000; font-weight:bold; ">else</span>
                <span style="color:#800000; ">"</span><span style="color:#0000e6; ">Unknown</span><span style="color:#800000; ">"</span>
    <span style="color:#800080; ">}</span>

    findLangType<span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">Java</span><span style="color:#800000; ">"</span><span style="color:#808030; ">)</span>
    findLangType<span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">Javascript</span><span style="color:#800000; ">"</span><span style="color:#808030; ">)</span>
    findLangType<span style="color:#808030; ">(</span><span style="color:#800000; ">"</span><span style="color:#0000e6; ">Typescript</span><span style="color:#800000; ">"</span><span style="color:#808030; ">)</span>
</pre>


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  <meta http-equiv="Content-Style-Type" content="text/css" />
  <meta name="generator" content="pandoc" />
  <title></title>
  <style type="text/css">code{white-space: pre;}</style>
  <style type="text/css">
div.sourceCode { overflow-x: auto; }
table.sourceCode, tr.sourceCode, td.lineNumbers, td.sourceCode {
  margin: 0; padding: 0; vertical-align: baseline; border: none; }
table.sourceCode { width: 100%; line-height: 100%; }
td.lineNumbers { text-align: right; padding-right: 4px; padding-left: 4px; color: #aaaaaa; border-right: 1px solid #aaaaaa; }
td.sourceCode { padding-left: 5px; }
code > span.kw { color: #007020; font-weight: bold; } /* Keyword */
code > span.dt { color: #902000; } /* DataType */
code > span.dv { color: #40a070; } /* DecVal */
code > span.bn { color: #40a070; } /* BaseN */
code > span.fl { color: #40a070; } /* Float */
code > span.ch { color: #4070a0; } /* Char */
code > span.st { color: #4070a0; } /* String */
code > span.co { color: #60a0b0; font-style: italic; } /* Comment */
code > span.ot { color: #007020; } /* Other */
code > span.al { color: #ff0000; font-weight: bold; } /* Alert */
code > span.fu { color: #06287e; } /* Function */
code > span.er { color: #ff0000; font-weight: bold; } /* Error */
code > span.wa { color: #60a0b0; font-weight: bold; font-style: italic; } /* Warning */
code > span.cn { color: #880000; } /* Constant */
code > span.sc { color: #4070a0; } /* SpecialChar */
code > span.vs { color: #4070a0; } /* VerbatimString */
code > span.ss { color: #bb6688; } /* SpecialString */
code > span.im { } /* Import */
code > span.va { color: #19177c; } /* Variable */
code > span.cf { color: #007020; font-weight: bold; } /* ControlFlow */
code > span.op { color: #666666; } /* Operator */
code > span.bu { } /* BuiltIn */
code > span.ex { } /* Extension */
code > span.pp { color: #bc7a00; } /* Preprocessor */
code > span.at { color: #7d9029; } /* Attribute */
code > span.do { color: #ba2121; font-style: italic; } /* Documentation */
code > span.an { color: #60a0b0; font-weight: bold; font-style: italic; } /* Annotation */
code > span.cv { color: #60a0b0; font-weight: bold; font-style: italic; } /* CommentVar */
code > span.in { color: #60a0b0; font-weight: bold; font-style: italic; } /* Information */
  </style>
  <link rel="stylesheet" href="style.css" type="text/css" />
</head>
<body>
