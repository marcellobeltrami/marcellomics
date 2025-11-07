---
title: 🐫-Perl's Legacy
published: true
---

### What is Perl and it’s explosion in the early millennium

![Perl 5 logo.](https://raw.githubusercontent.com/marcellobeltrami/marcellomics/main/_posts/post-assets/2025-11-07/perl.jpg)

*Perl 5 logo.*

Perl is a high level general purpose programming language that was developed by Larry Wall in 1987. It is often nickname the swiss-army knife of the internet, due to extensive availability of libraries. Common applications are seen in finance, system admin, networking, and bioinformatics.

Similarly to Python, it is commonly used as a glue language, where scripts often control multiple subroutines that are computationally more performant. It did gain popularity at the start of the millennium due to it’s impeccable string parsing capabilities, making the manipulation of long sequences of DNA, proteins and more very efficient.

```perl
#!/usr/bin/perl
use strict;
use warnings;

print "Hello, World!\n";
```

The further spread of Perl was incentivized by the ability to rapidly prototype scripts, which in research is commonly the case. For instance, built in nested structures, hash maps and references allow to represent heavily nested files such GTFs for annotation. Additionally regexes and string parsing have an extensive library allowing for the programmer to easily and quickly carry out motif search across long nucleic acid.

 Finally, Perl is designed to be highly portable, as once the code is written it can be easily run by the perl interpreter and translated to machine code . In addition, speed of language accounting for development time and stability results in great choice for researchers that do not have necessarily the skills of a full blown software engineer, but still like to apply themselves to programming.

But here the story takes a sad turn for Perl, as with the advent of bioinformatics oriented companies and academic institutes, other languages such as Python, R and more low level ones such as C++ or Rust, which have wider ecosystems overall. This was likely driven by the increase in C bindings for Python making it as performant as Perl, whilst maintaining ease of development.

![Common uses of Perl in 2025.](https://raw.githubusercontent.com/marcellobeltrami/marcellomics/main/_posts/post-assets/2025-11-07/PerlUses.png)

*Common uses of Perl in 2025.*

### Why Perl has been abandoned?

**The snake that ate the camel: Python** has been **optimised** and **widely adopted** across domains like data science, web development (with frameworks like Django and Flask), and system automation. Its emphasis on readability (enforced by significant white space) and its vast ecosystem of well-documented libraries often make it the preferred choice over Perl, especially for new projects.

**R for the win:**  **R** has become the **go-to for academic package development** and statistical computing. Its specialised tools and frameworks for data analysis, visualisation, and machine learning have made it the dominant language in those fields, pulling many users who might have previously relied on Perl for text processing and data manipulation.

**Low-Level Language Advancements:** The **increase in C++ stability** and the rise of **memory-safe languages such as Rust** have taken the place of Perl for certain high-performance or low-level systems programming tasks where speed and memory control are critical.
**Maintainability and Readability Challenges:**  The language's power and flexibility are a double-edged sword. **Perl syntax can be very terse**, allowing for multiple ways to accomplish the same task, often involving cryptic single-line commands (like those using regular expressions or the `$_` variable). This has led to the reputation of *"write once and never read,"* making it **difficult to maintain previous projects** or for new developers to onboard. In contrast, languages like Python prioritise a single, obvious way to do things.

### Why Perl is important now

Similar to how **COBOL** remains essential for banks and financial institutions due to decades of critical infrastructure, **legacy Perl code is still useful** and often running foundational systems, especially in older tech companies, ISPs, and large organisational The cost and risk of rewriting these massive, working code-bases are often prohibitive.

Perl excels at text manipulation and file processing, making it a powerful scripting tool. Many existing system administration scripts and core command-line utilities are still written and maintained in Perl. Additionally, **learning it helps to maintain previous tooling**. Developers with **Perl skills are in demand** to maintain and update these mission-critical legacy systems. While the volume of *new* Perl jobs is low, the *specialised need* for developers who can handle existing infrastructure ensures its ongoing, if niche, importance.

### Application to Perl in bioinformatics

**Bioperl is huge and has lots of useful functions** because it is a comprehensive, open-source collection of Perl modules designed to solve common bioinformatics tasks. It provides a standardised, object-oriented framework for handling biological data, including:

- **Sequence Manipulation:** Creating, reading, writing, and transforming sequence objects (DNA, RNA, protein).
- **File Format Handling:** Parsing and generating files in formats like FASTA, GenBank, EMBL, GFF, etc., using modules like `Bio::SeqIO`.
- **Database Interaction:** Accessing sequence data from public databases (like NCBI GenBank) and local indexes.
- **Tools Integration:** Running and parsing output from external tools like **BLAST**, ClustalW, and EMBOSS.
- **Sequence Features and Annotations:** Handling complex feature data associated with sequences.

```perl
#!/usr/bin/perl
use strict;
use warnings;
use Bio::SeqIO; # Module for Sequence Input/Output

# Check for required input file argument
die "Usage: perl script.pl <fasta_file>\n" unless @ARGV;

# Create a SeqIO object to read the FASTA file
# The -file argument is set to the first command-line argument ($ARGV[0])
my $seqio_obj = Bio::SeqIO->new(
    -file   => $ARGV[0],
    -format => 'fasta'
);

print "ID\tLength\tGC_Content\n";
print "-----------------------------------\n";

# Loop through each sequence object in the file
while (my $seq = $seqio_obj->next_seq) {
    # Access methods of the Bio::Seq object ($seq)
    my $id = $seq->id;
    my $len = $seq->length;

    # Calculate GC content using the dedicated method
    my $gc = $seq->percentage_gc_content;

    # Print the results
    printf "%s\t%d\t%.2f%%\n", $id, $len, $gc;
}
```

### Conclusion

- High level compiled at run time language
- Disappearing due to syntax and community shift to better supported languages
- Lots of useful legacy code due to early adoption
- Lots of useful bio libraries which are greate for sequences parsing.
