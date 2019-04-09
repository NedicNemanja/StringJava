# StringJava

<p>A parser and translator for a language supporting string operations. The language supports the concatenation operator over strings, function definitions and calls, conditionals (if-else i.e, every "if" must be followed by an "else"), and the following logical expressions:</p>
<ul>
<li>is-prefix-of (string1 prefix string2): Whether string1 is a prefix of string2.</li>
<li>is-suffix-of (string1 suffix string2): Whether string1 is a suffix of string2.</li>
</ul>
<p>All values in the language are strings.</p>
<p>The parser, based on a context-free grammar, will translate the input language into Java. With the will use JavaCUP for the generation of the parser combined with JFlex lexer.</p>
<p>Infer the desired syntax of the input and output languages from the examples below or with the grammar in the parser.cup file. The output language is a subset of Java so it can be compiled using the "javac" command and executed using the "java" command or online Java compilers like <a href="http://repl.it/languages/java">this</a>, if you want to test your output.</p>
<p>There is no type checking for the argument types or a check for the number of function arguments. We assume that the program input will always be semantically correct.</p>
<p> Moreover, for each function declaration of the input program, the translated Java program must contain an equivalent static method of the same name. Finaly, keep in mind that in the input language the function declations must precede all statements.</p>
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
