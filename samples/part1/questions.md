## Questions


* What steps are involved in making a Ruby scripts runnable as a 
command line utility? (i.e. directly runnable like `rake` or `gem`
rather than having to type `ruby my_script.rb`)

- add the shebang line, like #!/usr/bin/env ruby
- mark as executable, chmod +x []
- add its directory to the PATH, PATH=$PATH:[]

* What is `ARGF` stream used for in Ruby?

A stream that is the combination of all the input files to this script or if none, stdin

* What is `$?` used for in Bash/Ruby?

Return code from the last run command

* What does an exit status of zero indicate when a command line script 
terminates? How about a non-zero exit status?

0 - completed ok
~0 - not completed ok

* What is the difference between the `STDOUT` and `STDERR` output streams?

STDOUT - usual output from the process
STDERR - error output - eg where things went wrong or possible problems

* When executing shell commands from within a Ruby script, how can you capture
what gets written to `STDOUT`? How do you go about capturing both `STDOUT` and
`STDERR` streams?

Using Open3 lib to run the commands makes the in,out and process info available

* How can you efficiently write the contents of an input file 
to `STDOUT` with empty lines omitted? Being efficient in this context
means avoiding storing the contents of the input file in memory 
and processing the stream in a single pass.

# assuming ARGF does not store whole file in memory, otherwise just open file
# process each line at a time
ARGF.each_line do |line| 
  print line unless line.chomp.empty?
end



* How would you go about parsing command line arguments that contain a mixture
of flags and file arguments? (i.e. something like `ls -a -l foo/*.txt`)


Using the OptionParser library

Like so:

      params = {}
      parser = OptionParser.new 

      parser.on("-n") { params[:line_numbering_style] ||= :all_lines         }
      parser.on("-b") { params[:line_numbering_style]   = :significant_lines }
      parser.on("-s") { params[:squeeze_extra_newlines] = true               }

      files = parser.parse(argv)


* What features are provided by Ruby's `String` class to help with fixed width
text layouts? (i.e. right aligning a column of numbers, or left aligning a
column of text with some whitespace after it to keep the total 
column width uniform)

ljust/rjust and center

* Suppose your script encounters an error and has to terminate itself. What is
the idiomatic Unix-style way of reporting that the command did not run
successfully?

Using the return/exit code - 0/ok, non-0/an error, eg via exit(1)
