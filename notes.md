# Notes on Completing Ruby Koans

## About this codebase
1. What is a "koan"? A koan is a paradoxical question designed to provoke thought and introspection.
2. What is "rake"? Short for "Ruby make", rake is similar to "make" tool in C projects. It runs tasks defined in Rakefile. In the Rakefile, "task :default " for the default task run when executing "rake".
3. Why does executing "rake gen" generate the koans? The behavior for this command is defined by `task :gen => KOAN_FILES + [PROB_DIR + "/README.rdoc"]`, which tells rake to generate (or keep up-to-date) the KOAN_FILES, a list of filenames of the problem files (might not exist yet). "file tasks" specify how each file should be generated, having the format "file ...". In this case, it is
```
file koan_src.pathmap("#{PROB_DIR}/%f") => [PROB_DIR, koan_src] do |t|
    Koans.make_koan_file koan_src, t.name
end
```

## Koans - part 1
### strings
multiline strings
```
long_string = %{
hello
}
```

+= operator vs shovel (<<) operator: the later modifies the lhs, while the former creates a new object and assigns it to the lhs.