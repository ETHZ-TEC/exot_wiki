[:back:](/home)
---

# Utilities

Other provided utilities include:

1. Command-line parsing
1. Filesystem
1. Formatting
1. Logging
1. Memory
1. Meta-programming
1. Multi-threading
1. Synchronisation
1. Timing
1. Workers
1. Android specific JNI utilities

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::utilities`](#namespaceexot_1_1utilities) | Since std::filesystem is not yet mature enough to be included in some STL implementations, notably on Android, we have to rely on more standard Unix methods. The <dirent.h> should be available on most *nix platforms.
`namespace `[`exot::utilities::details`](#namespaceexot_1_1utilities_1_1details) | 
`namespace `[`exot::utilities::is_readable_from_stream std`](#namespaceexot_1_1utilities_1_1is__readable__from__stream_01std) | 
`namespace `[`exot::utilities::workers`](#namespaceexot_1_1utilities_1_1workers) | 
`namespace `[`exot::utilities::workers::policy_classes::synchronisation`](#namespaceexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation) | Mixin classes that provide a function `run()`, which executes a non-returning function with the desired synchronisation method.
`namespace `[`exot::utilities::workers::policy_classes::threading`](#namespaceexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading) | Mixin classes that allow setting thread parameters prior inside the used thread. They provide an `enforce()` function, which sets thread affinity and/or scheduling.
`namespace `[`fmt`](#namespacefmt) | Overloads that target the fmtlib directly
`namespace `[`nlohmann`](#namespacenlohmann) | 
`namespace `[`std`](#namespacestd) | These have to be accessible from the global namespace
`struct `[`exot::utilities::workers::policy_classes::synchronisation::BarrierSynchronisation::Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration) | 
`struct `[`exot::utilities::workers::policy_classes::synchronisation::NoSynchronisation::Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1_1Configuration) | 
`struct `[`exot::utilities::workers::policy_classes::threading::BasicThreads::Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1_1Configuration) | 
`struct `[`exot::utilities::workers::policy_classes::threading::PinnedThreads::Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration) | 
`struct `[`exot::utilities::workers::policy_classes::threading::SpecialisedThreads::Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration) | 
`struct `[`exot::utilities::AlignedAllocator::rebind`](#structexot_1_1utilities_1_1AlignedAllocator_1_1rebind) | 
`struct `[`exot::utilities::Logging::settings`](#structexot_1_1utilities_1_1Logging_1_1settings) | 

# namespace `exot::utilities` {#namespaceexot_1_1utilities}

Since std::filesystem is not yet mature enough to be included in some STL implementations, notably on Android, we have to rely on more standard Unix methods. The <dirent.h> should be available on most *nix platforms.

Globbing via <glob.h> is not available on Android platforms before API level 28, hence <regex>-based alternatives are provided.

__has_include macro is part of the C++17 standard. In the case when a platform does not provide the header file, and the contained functions are called, the linker will most likely complain about the lack of defined symbols.

These headers are available on Linux, Android, and Darwin platforms. If Windows support is desired in the future, a different mechanism for converting SchedulingPolicy enum to its respective platform-specific values will be needed, but will not impact client code.

On POSIX platforms, provide an STL-like wrapper for `nanosleep`.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`enum `[`Advice`](#namespaceexot_1_1utilities_1aeb849b1782b1d461631e01564e44895e)            | Enumeration for madvice(2) advice bits.
`enum `[`Symlinks`](#namespaceexot_1_1utilities_1af10d2366991225e19e246b49a00cd410)            | alias for struct stat
`enum `[`SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)            | A typed enum class which holds implementation-specific scheduling policy values.
`enum `[`TimingFenceType`](#namespaceexot_1_1utilities_1a8d8408c73eabacb3009c90f7a2105381)            | Enumeration for timing serialisation type.
`enum `[`TimingSourceType`](#namespaceexot_1_1utilities_1a7d9886836faa99c4a301171fc4eeb3db)            | Enumeration for timing source.
`public inline constexpr bool `[`is_valid_alignment`](#namespaceexot_1_1utilities_1aa3c7dfac11730d87c342d67c453f1dc4)`(std::size_t value) noexcept`            | Determines if a number is a valid alignment.
`public template<>`  <br/>`constexpr auto `[`make_aligned`](#namespaceexot_1_1utilities_1af6ee47359aa2fd798e3f390ec5fce62d)`(T t)`            | Makes an aligned version of a value.
`public inline void `[`advise`](#namespaceexot_1_1utilities_1a1747b84aa0322121fd40e3946f468760)`(void * address,std::size_t length,`[`Advice`](#namespaceexot_1_1utilities_1aeb849b1782b1d461631e01564e44895e)` advice)`            | Advises the kernel about how a memory range is used.
`public template<>`  <br/>`bool `[`operator!=`](#namespaceexot_1_1utilities_1a9e2691dc0d0c208cc9703ea3e544e390)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T1, Al1 > & lhs,const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T2, Al2 > & rhs) noexcept`            | Checks if allocators are not the same.
`public template<>`  <br/>`bool `[`operator==`](#namespaceexot_1_1utilities_1a52206fbc9fefec829f8c84a2902258fd)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T1, Al1 > & lhs,const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T2, Al2 > & rhs) noexcept`            | Checks if allocators are the same.
`public template<>`  <br/>`inline constexpr `[`larger_of_t`](#namespaceexot_1_1utilities_1ae76699e649bf5d3f7609eae176d5ec74)`< T1, T2 > `[`make_bitmask`](#namespaceexot_1_1utilities_1a806d2668c57cd5ef52b7651ade4f5d6b)`(T1 lower_bit,T2 upper_bit)`            | Makes a bitmask.
`public template<>`  <br/>`inline constexpr T1 `[`extract_with_bitmask`](#namespaceexot_1_1utilities_1a00ab7c9901b343a5e52bdb791eac474f)`(T1 value,T2 bitmask)`            | Extracts a value by applying a bitmask.
`public template<>`  <br/>`inline constexpr T1 `[`extract_bit_range`](#namespaceexot_1_1utilities_1aca68266a2d0b633df88a90f19690276f)`(T1 value,T2 lower_bit,T3 upper_bit)`            | 
`public template<>`  <br/>`inline constexpr void `[`set_bit`](#namespaceexot_1_1utilities_1ae3eb6767de882a6fb7264e2952f969d4)`(T & value,B bit)`            | 
`public template<>`  <br/>`inline constexpr void `[`set_bits`](#namespaceexot_1_1utilities_1a263432f9cd5c8807e5c061c257e793e2)`(T & value,Bs... bits)`            | 
`public template<>`  <br/>`inline constexpr void `[`set_bit_range`](#namespaceexot_1_1utilities_1a88ae6d6d37f474ce6aea5f6af133423a)`(T1 & value,T2 lower_bit,T3 upper_bit)`            | 
`public template<>`  <br/>`inline constexpr T `[`get_bit`](#namespaceexot_1_1utilities_1ad4e8a57bb27e1512cba249f9d5d30ac2)`(T value,B bit)`            | 
`public template<>`  <br/>`inline constexpr void `[`clear_bit`](#namespaceexot_1_1utilities_1a523396f307d880fdfb9e21820e43c4dc)`(T & value,B bit)`            | 
`public template<>`  <br/>`inline constexpr void `[`clear_bits`](#namespaceexot_1_1utilities_1a391b9d75257c02d549309612b2f758e5)`(T & value,Bs... bits)`            | 
`public template<>`  <br/>`inline constexpr void `[`clear_bit_range`](#namespaceexot_1_1utilities_1a36b25f5854164b878e0b0c65a310401a)`(T1 & value,T2 lower_bit,T3 upper_bit)`            | 
`public template<>`  <br/>`inline constexpr void `[`toggle_bit`](#namespaceexot_1_1utilities_1a0cd350985f3dbf589e72e244210ff85a)`(T & value,B bit)`            | 
`public template<>`  <br/>`inline constexpr void `[`toggle_bits`](#namespaceexot_1_1utilities_1a08b4796d7930eea139c419c8c1acbe5b)`(T & value,Bs... bits)`            | 
`public template<>`  <br/>`inline constexpr void `[`toggle_bit_range`](#namespaceexot_1_1utilities_1a5f1e588169ef4c28046edb9baa20383a)`(T1 & value,T2 lower_bit,T3 upper_bit)`            | 
`public template<>`  <br/>`inline bool `[`test_bit`](#namespaceexot_1_1utilities_1a449e921e92b712b70ce24ffb41c981d9)`(T value,B bit)`            | 
`public template<>`  <br/>`inline bool `[`test_bits`](#namespaceexot_1_1utilities_1af5b6d1cf86efb84c23609e485b5bd983)`(T value,Bs... bits)`            | 
`public template<>`  <br/>`inline constexpr bool `[`test_bit_range`](#namespaceexot_1_1utilities_1ae83329519e9b7f7f2ad77e78d827e4d9)`(T1 value,T2 lower_bit,T3 upper_bit)`            | 
`public template<>`  <br/>`inline constexpr int `[`hamming_weight`](#namespaceexot_1_1utilities_1a4242685386b06d67c7ff7490b629bf92)`(T value)`            | Return the hamming weight of a number, the count of bits set to 1.
`public template<>`  <br/>`inline constexpr int `[`parity`](#namespaceexot_1_1utilities_1ad990f69f531a2f2ccbc7128316f518e6)`(T value)`            | Return the parity of the value (evenness/oddness of an integer)
`public template<>`  <br/>`inline constexpr int `[`trailing_zero_bits`](#namespaceexot_1_1utilities_1a8771ead3f27e092a8efaddc480931fd3)`(T value)`            | Gets the number of trailing zero bits in an unsigned integer.
`public template<>`  <br/>`inline constexpr int `[`leading_zero_bits`](#namespaceexot_1_1utilities_1a304a1ca5cd9b82296e553d6e3ffc292b)`(T value)`            | Gets the number of leading zero bits in an unsigned integer.
`public template<>`  <br/>`inline constexpr std::size_t `[`next_set_bit`](#namespaceexot_1_1utilities_1aa47525741009521ecf68fb28530796b8)`(T value,std::size_t bit)`            | Gets the position of the next set bit in an unsigned integer.
`public template<>`  <br/>`inline constexpr void `[`loop_through_set_bits`](#namespaceexot_1_1utilities_1a28b7ffc68ae5561ee6d75a2b415eed6a)`(T value,F && callable)`            | Executes a callable with indeces of set bits in a value.
`public template<>`  <br/>`inline void `[`set_json`](#namespaceexot_1_1utilities_1a47e792a1b7a5e283d2a19c2d05bda20f)`(const `[`JsonConfig`](#classexot_1_1utilities_1_1JsonConfig)` & config,Ts &&... ts)`            | Sets the JSON file in multiple configurables.
`public template<>`  <br/>`inline void `[`configure`](#namespaceexot_1_1utilities_1ab0ab2922d2b0aba8a69b9398ce9074b5)`(const `[`JsonConfig`](#classexot_1_1utilities_1_1JsonConfig)` & config,Ts &&... ts)`            | Sets the JSON file in multiple configurables and configures them.
`public template<>`  <br/>`inline void `[`get_from_json_to`](#namespaceexot_1_1utilities_1a60cbd26352cb380d79a6ae33103f67ac)`(const nlohmann::json & json,K key,T & ref)`            | Attempts to assign a value from a json object to a referenced variable, using the provided key.
`public template<>`  <br/>`inline void `[`get_from_json_to`](#namespaceexot_1_1utilities_1aa66a50d55ab96801ce1932144fb0df1a)`(const nlohmann::json & json,const char * key,T & ref)`            | Temporary partial specialisation for get_from_json_to and const char* key.
`public template<>`  <br/>`inline void `[`get_from_json_to`](#namespaceexot_1_1utilities_1a5ecba66ecbe970436b4e4dffe5ca086d)`(const nlohmann::json & json,const nlohmann::json::json_pointer & key,T & ref)`            | Temporary partial specialisation for get_from_json_to and a JSON pointer.
`public template<>`  <br/>`inline void `[`set_json`](#namespaceexot_1_1utilities_1a44565970841862f6fb492ffe40e3329a)`(U json,Ts &&... ts)`            | Sets the JSON object in configurables.
`public template<>`  <br/>`inline void `[`configure`](#namespaceexot_1_1utilities_1a5d264c66da8e5b3e2b1d83a66de240cb)`(U json,Ts &&... ts)`            | Sets the JSON object in configurables and configures them.
`public template<>`  <br/>`inline void `[`set_json`](#namespaceexot_1_1utilities_1a1cf2c2e7f520d7130a0820a06cb944c5)`(nlohmann::json::const_reference root,Ts &&... ts)`            | Sets the JSON file in multiple configurables.
`public template<>`  <br/>`inline void `[`only_configure`](#namespaceexot_1_1utilities_1af64d0b3e99802cf1386ba81b9a360308)`(Ts &&... ts)`            | Configures multiple configurables.
`public template<>`  <br/>`inline void `[`configure`](#namespaceexot_1_1utilities_1ab22a772f5cf0b07b0d2b58a3bbd28dd4)`(nlohmann::json::const_reference root,Ts &&... ts)`            | Sets the JSON file in multiple configurables and configures them.
`public template<>`  <br/>`void `[`sort_and_deduplicate`](#namespaceexot_1_1utilities_1a66ed3e57b283b6b861f4fe75a54f2a82)`(std::vector< T > & vector)`            | Sort and deduplicate a vector of comparable elements.
`public void `[`bootstrap_cores`](#namespaceexot_1_1utilities_1a31beaa3c9014604091575a5d8f2b401c)`(std::vector< unsigned > & cores)`            | Bootstrap a vector of cores.
`public template<>`  <br/>`std::string `[`generate_header`](#namespaceexot_1_1utilities_1a976ffe281ad359722fd9172d753c38f7)`(Ts &&... ts)`            | Generate a header for application logging purposes.
`public template<>`  <br/>`inline constexpr Enum `[`operator\|`](#namespaceexot_1_1utilities_1aa828d3adbee98a5783f6c1fc8a292ebf)`(Enum lhs,Enum rhs)`            | Bit-wise "or" operator overload.
`public template<>`  <br/>`inline constexpr Enum & `[`operator\|=`](#namespaceexot_1_1utilities_1ae81202afa3a7e88b1cbf2dd01cc89d62)`(Enum lhs,Enum rhs)`            | Bit-wise "or" assignment operator overload.
`public template<>`  <br/>`inline constexpr Enum `[`operator&`](#namespaceexot_1_1utilities_1aafcf79262999e838b7de7ecf70a591f7)`(Enum lhs,Enum rhs)`            | Bit-wise "and" operator overload.
`public template<>`  <br/>`inline constexpr Enum & `[`operator&=`](#namespaceexot_1_1utilities_1a60408208f1761967016cade61a77d7d7)`(Enum lhs,Enum rhs)`            | Bit-wise "and" assignment operator overload.
`public template<>`  <br/>`inline constexpr Enum `[`operator^`](#namespaceexot_1_1utilities_1ab1ec359abf8aff73e508ea436f913e76)`(Enum lhs,Enum rhs)`            | Bit-wise "xor" operator overload.
`public template<>`  <br/>`inline constexpr Enum & `[`operator^=`](#namespaceexot_1_1utilities_1a3e638c61523d7f6161e3b05d8d79a68f)`(Enum lhs,Enum rhs)`            | Bit-wise "xor" assignment operator overload.
`public template<>`  <br/>`inline constexpr Enum & `[`operator~`](#namespaceexot_1_1utilities_1a16c508b10990b586d09fbd9842002db5)`(Enum e)`            | Bit-wise "not" operator overload.
`public bool `[`is_readable`](#namespaceexot_1_1utilities_1a491635ae7135842c9e2089fd47ef2224)`(const std::string & path)`            | Checks if a provided file can be read.
`public bool `[`exists`](#namespaceexot_1_1utilities_1ab8e2431393863eb11908c87faf4a9de7)`(const std::string & path)`            | Checks if a provided path exists.
`public bool `[`is_directory`](#namespaceexot_1_1utilities_1a5a74a2aab967c8bc33eb83e54cbd481d)`(const std::string & path)`            | Determines if a path is a directory.
`public auto `[`get_stat`](#namespaceexot_1_1utilities_1a77c8233e3606b643e4de8f29c0d9b879)`(const std::string & path)`            | Gets the sys/stat.h 'stat' struct for a path.
`public bool `[`all_readable`](#namespaceexot_1_1utilities_1adda329da05ce7089e8484b20532f5b4c)`(const std::vector< std::string > & paths)`            | Checks if all provided files can be accessed.
`public bool `[`is_empty`](#namespaceexot_1_1utilities_1aedaa579544f1d723acc13dab064ff63f)`(const std::string & file_path)`            | Determines if a file is empty.
`public std::vector< std::string > `[`remove_unreadable`](#namespaceexot_1_1utilities_1a9bd010519c0d52f3b96680890c58d06b)`(std::vector< std::string > & paths)`            | Removes unreadable files from a vector of paths.
`public template<>`  <br/>`inline auto `[`get_value_from_file`](#namespaceexot_1_1utilities_1a644204a275e889767cf49d257a11ebc8)`(const std::string & path)`            | Get a value of certain type from file.
`public auto `[`get_long_string_value_from_file`](#namespaceexot_1_1utilities_1a7aa994ed10f5501386883214ec2a5016)`(const std::string & path)`            | Gets the long string value from file.
`public auto `[`get_string_value_from_file`](#namespaceexot_1_1utilities_1a97b91fa578b36e75133e7c502c36ce00)`(const std::string & path)`            | Gets a string value from a file.
`public template<>`  <br/>`std::vector< std::basic_string< CharT > > `[`split_string`](#namespaceexot_1_1utilities_1aa9d044c4fc5fd2457d2c9b49b42c561f)`(const std::basic_string< CharT > & string,CharT delimiter)`            | Splits a string using a delimeter.
`public template<>`  <br/>`std::basic_string< CharT > `[`join_strings`](#namespaceexot_1_1utilities_1aeda506b3b1f0ba00e4048ba861a60c7d)`(const std::vector< std::basic_string< CharT >> & strings,CharT delimiter)`            | Joins a vector of strings into a single delimited string.
`public template<>`  <br/>`std::string `[`wrap`](#namespaceexot_1_1utilities_1a359b7f814215bdd7682e2fef260fe2ee)`(const std::basic_string< CharT > & to_wrap,size_t width,size_t indent)`            | Wraps a string to a desired number of columns.
`public template<>`  <br/>`std::string `[`indent`](#namespaceexot_1_1utilities_1a9cfad0c2e6f19b757f89803686ea5dfa)`(const std::basic_string< CharT > & to_indent,size_t indent,bool wrap)`            | 
`public template<>`  <br/>`std::string `[`trim_string`](#namespaceexot_1_1utilities_1a455fb3ce629172a9fb900b7b7080a606)`(const std::basic_string< CharT > & to_trim,const std::basic_string< CharT > & trim_characters)`            | Trim characters at front and back of the string, mostly for whitespace.
`public template<>`  <br/>`std::string `[`trim_string`](#namespaceexot_1_1utilities_1a84005e89e742a3913b1d379d7b4ce296)`(const std::basic_string< CharT > & to_trim,const CharT * trim_characters)`            | 
`public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1aa7a63337367d561f61e7b26947d867e4)`(const std::basic_string< CharT > & to_collapse,const std::basic_string< CharT > & fill_characters,const std::basic_string< CharT > & collapse_characters)`            | Collapse characters present in a string, preferably whitespace.
`public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1a30f0a0f656d2d68769fa808c35f892ce)`(const std::basic_string< CharT > & to_collapse,const std::basic_string< CharT > & fill_characters,const CharT * collapse_characters)`            | 
`public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1a49cd2d9c3e1268f3add063a98a328a8d)`(const std::basic_string< CharT > & to_collapse,const CharT * fill_characters,const CharT * collapse_characters)`            | 
`public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1aa9de72e523edcf6af82f7a1700277370)`(const std::basic_string< CharT > & to_collapse,const CharT * fill_characters,const std::basic_string< CharT > & collapse_characters)`            | 
`public inline unsigned `[`extract_number`](#namespaceexot_1_1utilities_1aa9e40ef7dea6fc0fa3d96b5d804df61d)`(const std::string & string)`            | Extract the first occurence of a positive number from a string.
`public inline std::vector< unsigned > `[`extract_numbers`](#namespaceexot_1_1utilities_1afd0c8ca7867d0eeb862d5fb44db51f2f)`(const std::string & in)`            | Extract the all occurences of positive numbers from a string.
`public inline unsigned `[`read_hex_value`](#namespaceexot_1_1utilities_1af38ee523f89c67ca601e3fadc3b24184)`(const std::string & string)`            | Helper function for obtaining an unsigned number from a hexadecimal string notation, also without the leading '0x'.
`public template<>`  <br/>`std::string `[`ratio_to_string`](#namespaceexot_1_1utilities_1a273a667f73f461eeef7c8384386d3780)`(std::ratio< Num, Den > ratio) noexcept`            | Get a string description of a ratio.
`public template<>`  <br/>`std::string `[`duration_unit`](#namespaceexot_1_1utilities_1a77629eee17cffdca74b6506eca965292)`(std::chrono::duration< Rep, Period >)`            | Get a unit prefix of a duration period.
`public template<>`  <br/>`std::string `[`duration_to_string`](#namespaceexot_1_1utilities_1a0026502c0e48f91e8c28b91b379413fd)`(std::chrono::duration< Rep, Period > duration)`            | Print a duration with its unit.
`public template<>`  <br/>`constexpr void `[`const_for`](#namespaceexot_1_1utilities_1ab1f46f0d798d093a4221294da0f717e6)`(Callable && func)`            | A compile-time for-loop.
`public template<>`  <br/>`constexpr void `[`for_each`](#namespaceexot_1_1utilities_1ab52416714fd0b45168ed6ff929eb8a08)`(std::tuple< Ts... > && tuple,Callable && func)`            | Apply a function to each tuple element.
`public template<>`  <br/>`auto `[`tail`](#namespaceexot_1_1utilities_1ae63930670c418e9393f98f648a078fe6)`(std::tuple< Ts... > && value)`            | 
`public template<>`  <br/>`auto `[`zip`](#namespaceexot_1_1utilities_1a84d5c61305b2449309cec8b5079cd064)`(T && t,Ts &&... ts)`            | Zips multiple tuples together.
`public template<>`  <br/>`auto `[`zip_fwd`](#namespaceexot_1_1utilities_1a05ec94d6ca96f43b118e455e0939412e)`(T && t,Ts &&... ts)`            | Zips multiple tuples together by forwarding values.
`public template<>`  <br/>`auto `[`mean_and_deviation`](#namespaceexot_1_1utilities_1a7a69efeca7d0189affb1f54dd9be6fa0)`(const std::vector< T > & input)`            | Calculates the mean and standard deviation of values in a container.
`public template<>`  <br/>`constexpr auto `[`slice`](#namespaceexot_1_1utilities_1a6fd0e700dde7e74da01a061a886afa8a)`(const T & container,std::size_t lower,std::size_t upper)`            | Gets a slice of an interable container.
`public template<>`  <br/>`constexpr auto `[`percentile`](#namespaceexot_1_1utilities_1a10667f9bac01143ca54a86176397fe80)`(T container,double value)`            | Gets a percentile of values in a container.
`public template<>`  <br/>`constexpr auto `[`percentile_sort_in_place`](#namespaceexot_1_1utilities_1a8598f09e55e3d217c7982c97437a60e2)`(T & container,double value)`            | Gets a percentile of values in a container, sorting it in place.
`public template<>`  <br/>`constexpr auto `[`percentile_range`](#namespaceexot_1_1utilities_1a4e56e0c83a1ad5af8d3aefdf9f4fd0d8)`(T container,double lower,double upper)`            | Gets a slice of a container in percentile limits.
`public template<>`  <br/>`inline constexpr bool `[`is_power_of_2`](#namespaceexot_1_1utilities_1a3d8f91f6680b5f0b83721f29e991730d)`(T value) noexcept`            | Determines if power of 2.
`public template<>`  <br/>`inline constexpr bool `[`is_one_of`](#namespaceexot_1_1utilities_1abe6e879f78cf2de7b6ade50435865aa9)`(T && t,Ts &&... ts)`            | Determines if a value is within a set of other values.
`public template<>`  <br/>`inline constexpr bool `[`is_none_of`](#namespaceexot_1_1utilities_1a77f933ffe1d47f86ac78fda77b69b1c1)`(T && t,Ts &&... ts)`            | Determines if a value is not in a set of other values.
`public template<>`  <br/>`auto `[`contains`](#namespaceexot_1_1utilities_1a8eafda304811f6c707dc0ee5274eb662)`(typename T::value_type v,const T & container)`            | Check if a container contains an element.
`public template<>`  <br/>`constexpr bool `[`is_greater`](#namespaceexot_1_1utilities_1ad1fa959c908c36f621995c4494ec31bc)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`constexpr bool `[`is_greater_or_equal`](#namespaceexot_1_1utilities_1ad489950b8b27f67148f287dcab4fe250)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`constexpr bool `[`assert_is_greater`](#namespaceexot_1_1utilities_1ac24a007dffab9f51aeac19b5c5efa73b)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`constexpr bool `[`assert_is_greater_or_equal`](#namespaceexot_1_1utilities_1a90ddafe9fa6a46e8df903bf2af721078)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`constexpr bool `[`is_smaller`](#namespaceexot_1_1utilities_1a28436e4afc9d6961696eb460dbfb5aa3)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`constexpr bool `[`is_smaller_or_equal`](#namespaceexot_1_1utilities_1a3789a4a1fddd3bf13df62b1811f5dfe5)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`constexpr bool `[`assert_is_smaller`](#namespaceexot_1_1utilities_1a486588c53a98389088eb84b58f905456)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`constexpr bool `[`assert_is_smaller_or_equal`](#namespaceexot_1_1utilities_1a6b3e316a8dc7e2bf98b00d9de4a7173c)`(T t,Ts &&... ts)`            | 
`public template<>`  <br/>`inline  `[`__attribute__`](#namespaceexot_1_1utilities_1a97737d9b68d855784bed53f42770e971)`((always_inline)) const`            | Helper to prevent the compiler from optimising a variable.
`public template<>`  <br/>`inline  `[`__attribute__`](#namespaceexot_1_1utilities_1aabb32788e9721b5cb61fc214df923082)`((always_inline))`            | Alias for US spelling of 'optimise'.
`public template<>`  <br/>`constexpr bool `[`is_constexpr`](#namespaceexot_1_1utilities_1aaffdbcf77206e7cbc043659c60e966cb)`(Ts &&... ts)`            | Determines if values or function returns are constexpr.
`public template<>`  <br/>`std::istream & `[`operator>>`](#namespaceexot_1_1utilities_1a667d1c0a022b6dcdecfa51f4d0851c42)`(std::basic_istream< CharT, CharTraitsT > & stream,std::chrono::duration< Rep, Period > & duration)`            | Input stream operator overload for reading durations.
`public template<>`  <br/>`std::tuple< Current, Rest... > `[`read_tuple`](#namespaceexot_1_1utilities_1aa715562a4af5f4f3c8cf106103f62f80)`(std::basic_istream< CharT, CharTraitsT > & stream)`            | Reads a tuple from an istream.
`public inline constexpr unsigned long long `[`operator""_KiB`](#namespaceexot_1_1utilities_1a14c6657637682b32516d099b05d36589)`(unsigned long long v)`            | Converts a kibibytes value to bytes.
`public inline constexpr unsigned long long `[`operator""_MiB`](#namespaceexot_1_1utilities_1a354deb2ddbbfccf7a5ae4cf6e64e89bc)`(unsigned long long v)`            | Converts a mebibytes value to bytes.
`public inline constexpr unsigned long long `[`operator""_GiB`](#namespaceexot_1_1utilities_1ab4aeb268b9065a03b6addcbeb0c8b428)`(unsigned long long v)`            | Converts a gibibytes value to bytes.
`public void `[`append_to_filename`](#namespaceexot_1_1utilities_1ab813a8b40662932691338ca0d76ba853)`(std::string & file_path,const std::string & to_append)`            | Appends a string to the filename.
`public void `[`append_timestamp_to_filename`](#namespaceexot_1_1utilities_1a2e5799143f95382615e0ae8bf83d8148)`(std::string & file_path)`            | Appends a timestamp to a filename.
`public template<>`  <br/>`auto `[`cli_wrapper`](#namespaceexot_1_1utilities_1a7e78562cba2977aa14bcd76022fb56f8)`(int argc,char ** argv)`            | Provides a cli main wrapper for typical applications.
`public std::optional< std::string > `[`get_kernel_version`](#namespaceexot_1_1utilities_1a7f0409a861baf75342dc109450e6ec52)`()`            | Gets the kernel version.
`public std::vector< std::string > `[`get_cpuinfo_keys`](#namespaceexot_1_1utilities_1a5443629202666c4e38fc291772276060)`()`            | Gets all the available cpuinfo keys.
`public std::optional< std::map< std::string, std::string > > `[`get_cpuinfo_as_map`](#namespaceexot_1_1utilities_1ae23243ed6562e9275a85641e1c6dc850)`(unsigned cpu)`            | Gets the cpuinfo key-value pairs as a map for a specific cpu.
`public std::vector< std::map< std::string, std::string > > `[`get_complete_cpuinfo_as_map_array`](#namespaceexot_1_1utilities_1a57323b071d00e7590fa45600c6493af0)`()`            | Gets the complete cpuinfo as map array.
`public std::optional< std::string > `[`get_cpuinfo_value`](#namespaceexot_1_1utilities_1a05f9a1a524fa6a26c04edf4562ba78fa)`(unsigned cpu,const std::string & key)`            | Gets the cpuinfo value for a given key for a specific cpu.
`public std::vector< std::string > `[`get_cpuinfo_values`](#namespaceexot_1_1utilities_1a48d6bab28cb922fe34b999e7c8786f13)`(const std::string & key)`            | Gets the cpuinfo values for a given key for all cpus.
`public unsigned `[`get_cpu_count`](#namespaceexot_1_1utilities_1a33adcc8cddf191ac571f017eb9813463)`()`            | Gets the cpu count.
`public unsigned `[`get_thread_count`](#namespaceexot_1_1utilities_1a72a1a329722d10c1b7e551c7126ea9a5)`()`            | Gets the thread count.
`public unsigned `[`get_core_count`](#namespaceexot_1_1utilities_1acae1bd2eec2587e6c4bf940074c652e8)`()`            | Gets the core count.
`public unsigned `[`get_socket_count`](#namespaceexot_1_1utilities_1a109d7bb24dc351cbed069d29153e4a0a)`()`            | Gets the socket count.
`public unsigned `[`get_thread_per_core`](#namespaceexot_1_1utilities_1a41e006e0e988cbe914c546f58a9944de)`()`            | Gets the thread per core. Derived from get_thread_count and get_core_count.
`public unsigned `[`get_core_per_socket`](#namespaceexot_1_1utilities_1a9ae0e678ad5db0c2f8c14514c1c864e8)`()`            | Gets the core per socket. Derived from get_core_count and get_socket_count.
`public const char * `[`get_target_architecture`](#namespaceexot_1_1utilities_1ad32fed5bbf796015525711cff54ba814)`() noexcept`            | Gets the target architecture. Returns a compile-time value.
`public std::optional< std::string > `[`get_cpu_vendor`](#namespaceexot_1_1utilities_1a4d564f211ea602094b44648f1e669ab4)`(unsigned cpu)`            | Gets the cpu vendor of a specific cpu.
`public std::optional< std::string > `[`get_cpu_model`](#namespaceexot_1_1utilities_1af38813feffb718987234632834a80b19)`(unsigned cpu)`            | Gets the cpu model of a specific cpu.
`public std::optional< std::vector< std::string > > `[`get_unique_cpu_models`](#namespaceexot_1_1utilities_1ab200e0cd33037c72afefed357806106a)`()`            | Gets all unique cpu models and their associated cpus.
`public std::optional< std::string > `[`get_cpu_flags`](#namespaceexot_1_1utilities_1ad85d5a65320180280b0370acaad5e6b9)`(unsigned cpu)`            | Gets the cpu flags of a specific cpu.
`public std::optional< std::vector< std::string > > `[`get_cpu_flags_array`](#namespaceexot_1_1utilities_1a4736afc3ee64f00045d0b6747f7b7722)`(unsigned cpu)`            | Gets the cpu flags as an array for a specific cpu.
`public std::optional< std::string > `[`get_scaling_governor`](#namespaceexot_1_1utilities_1a1208e4b3b1783b5e826b75f9970ad82b)`(unsigned cpu)`            | Gets the scaling governor of a specific cpu.
`public std::optional< std::array< unsigned long, 2 > > `[`get_cpu_frequencies`](#namespaceexot_1_1utilities_1a50b92d34ed4543b5dbe35c6dcd927ae5)`(unsigned cpu)`            | Gets the min and max cpu frequencies of a specific cpu. The frequencies are given in Hz.
`public std::optional< unsigned long > `[`get_min_cpu_frequency`](#namespaceexot_1_1utilities_1ae3f06867e9c4f2051024d1056ec1c558)`(unsigned cpu)`            | Gets the minimum cpu frequency of a specific cpu. The frequency is given in Hz.
`public std::optional< unsigned long > `[`get_max_cpu_frequency`](#namespaceexot_1_1utilities_1a88c6c940ac2585fdfa3b9298bf15e114)`(unsigned cpu)`            | Gets the maximum cpu frequency of a specific cpu. The frequency is given in Hz.
`public std::string `[`get_online_cpus`](#namespaceexot_1_1utilities_1abf6b4e44b578cbb1fd96535ea4296a91)`()`            | Gets the string representation of online cpus.
`public std::string `[`get_offline_cpus`](#namespaceexot_1_1utilities_1acc04c42127b5cc88c8af00a168a21a28)`()`            | Gets the string representation of offline cpus.
`public std::string `[`get_possible_cpus`](#namespaceexot_1_1utilities_1a6e4a71c86b85e5c902a89233b1175307)`()`            | Gets the string representation of possible cpus. Possible cpus are those that can be either brought online, or made offline.
`public std::vector< bool > `[`get_online_cpus_array`](#namespaceexot_1_1utilities_1a56331ec82c793b3502577d9ae71e0dd7)`()`            | Gets the online cpus array.
`public bool `[`is_cpu_online`](#namespaceexot_1_1utilities_1a02d352f68375595a85bce88ce8b006fe)`(unsigned int cpu)`            | Determines if a cpu online.
`public std::optional< std::string > `[`get_topology_value`](#namespaceexot_1_1utilities_1a6dbb1392597134a70349e5c7ad0c93bd)`(unsigned cpu,const std::string & key)`            | Gets the topology value given a valid key for a specific cpu.
`public std::optional< unsigned > `[`get_core_id`](#namespaceexot_1_1utilities_1a01f85d50c8c0b3364cb69215e52050df)`(unsigned cpu)`            | Gets the core identifier of a specific cpu.
`public std::optional< unsigned > `[`get_core_siblings`](#namespaceexot_1_1utilities_1af652e8d4b2409c25f4fd45d0e751e6d6)`(unsigned cpu)`            | Gets the core siblings of a specific cpu.
`public std::optional< std::vector< unsigned > > `[`get_core_siblings_array`](#namespaceexot_1_1utilities_1a9d56a36fe956612ebfd7234c17bf957b)`(unsigned cpu)`            | Gets the core siblings as an array for a specific cpu.
`public std::optional< unsigned > `[`get_core_siblings_count`](#namespaceexot_1_1utilities_1a82a144e588b830b4ba9d9da554f716e8)`(unsigned cpu)`            | Gets the core siblings count of a specific cpu.
`public std::optional< unsigned > `[`get_physical_package_id`](#namespaceexot_1_1utilities_1a4652c75c01183d781a7ae46e1574dc14)`(unsigned cpu)`            | Gets the physical package identifier of a specific cpu.
`public std::optional< unsigned > `[`get_thread_siblings`](#namespaceexot_1_1utilities_1a48c7f27068b7ac329ebb6f96dc2f3817)`(unsigned cpu)`            | Gets the thread siblings of a specific cpu.
`public std::optional< std::vector< unsigned > > `[`get_thread_siblings_array`](#namespaceexot_1_1utilities_1a2f7e29ee4047c65a4a486281cf36e5ee)`(unsigned cpu)`            | Gets the thread siblings as an array for a specific cpu.
`public std::optional< unsigned > `[`get_thread_siblings_count`](#namespaceexot_1_1utilities_1afac4a6b1c697925061c5cbfe90058384)`(unsigned cpu)`            | Gets the thread siblings count of a specific cpu.
`public std::optional< std::map< std::string, std::string > > `[`get_cpu_topology_map`](#namespaceexot_1_1utilities_1a507f3f9f6c8fb67bb3f54d6765b52598)`(unsigned cpu)`            | Gets the complete cpu topology as a map for a specific cpu.
`public std::optional< std::string > `[`get_cpu_topology`](#namespaceexot_1_1utilities_1aacddd09873395f1dee836823fb038e26)`(unsigned cpu)`            | Gets the serialised cpu topology of a specific cpu as a string. The result is JSON-like formatted.
`public std::vector< std::string > `[`get_complete_topology`](#namespaceexot_1_1utilities_1afa95e09e87c7959ff0188fac50a3c56d)`()`            | Gets a description of the complete topology for all cpus. The result is JSON-like formatted.
`public std::string `[`thread_info`](#namespaceexot_1_1utilities_1a5a4e5777ca7af7172e5c24ebeaef9db5)`()`            | Produce an info string containing information about the current thread.
`public template<>`  <br/>`auto `[`timeit`](#namespaceexot_1_1utilities_1a2e5b48f12c277da73e7d0d79e5c4923a)`(Callable && callable,Args &&... args)`            | Time the execution of a callable using timestamp counters.
`public template<>`  <br/>`inline static void `[`busysleep`](#namespaceexot_1_1utilities_1a8fb5c1ba9a5d78a7d465daf712f3142c)`(const std::chrono::duration< Rep, Period > & duration)`            | Busy sleep function, continuously checking if time has elapsed.
`public static std::tm `[`get_utc_time`](#namespaceexot_1_1utilities_1ac7298346d5ab650a39446d3de68f8ab3)`()`            | Gets the UTC time as a C time struct.
`public static std::tm `[`get_local_time`](#namespaceexot_1_1utilities_1ae56ada3ebdb04080b9b2d9abb1fd5345)`()`            | Gets the local time as a C time struct.
`public template<>`  <br/>`inline auto `[`default_timing_facility`](#namespaceexot_1_1utilities_1af5a8018a7799ad8bcbd1441bcc20cd60)`(Args &&... args)`            | The default timeing facility.
`public template<>`  <br/>`constexpr auto `[`to_underlying_type`](#namespaceexot_1_1utilities_1ac9851a52cd02e651bd5e351e1eec0c19)`(T t)`            | Casts a type (e.g. scoped enum class) to its underlying type.
`public bool `[`is_cpu_online`](#namespaceexot_1_1utilities_1a80de8e36bf8759179c5b36343df3b884)`(unsigned cpu)`            | 
`class `[`exot::utilities::Barrier`](#classexot_1_1utilities_1_1Barrier) | The barrier thread synchronisation primitive, also known as a randezvous point.
`class `[`exot::utilities::CLI`](#classexot_1_1utilities_1_1CLI) | Class providing the command line interface.
`class `[`exot::utilities::JsonConfig`](#classexot_1_1utilities_1_1JsonConfig) | 
`class `[`exot::utilities::Logging`](#classexot_1_1utilities_1_1Logging) | Class that encapsulates all logging options and is responsible for creating loggers.
`class `[`exot::utilities::TimeKeeper`](#classexot_1_1utilities_1_1TimeKeeper) | Class used for keeping track of sleep time and offsets.
`struct `[`exot::utilities::aligned_t`](#structexot_1_1utilities_1_1aligned__t) | Aligned type wrapper.
`struct `[`exot::utilities::AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator) | Aligned allocator to use with STL containers.
`struct `[`exot::utilities::bad_alloc`](#structexot_1_1utilities_1_1bad__alloc) | 
`struct `[`exot::utilities::configurable`](#structexot_1_1utilities_1_1configurable) | Mixin for use in CRTP patterns to introduce configurability to compatible classes.
`struct `[`exot::utilities::configurable_base`](#structexot_1_1utilities_1_1configurable__base) | Base class for configurable types.
`struct `[`exot::utilities::is_writable_to_stream< T, std::ostream, std::void_t< decltype(std::declval< std::ostream & >()<< std::declval< T & >())> >`](#structexot_1_1utilities_1_1is__writable__to__stream_3_01T_00_01std_1_1ostream_00_01std_1_1void__5d1df126fd77cfd63df8a5108f424957) | 
`struct `[`exot::utilities::enum_operations_enabled`](#structexot_1_1utilities_1_1enum__operations__enabled) | Type trait to enable bit-wise operations for an Enum.
`struct `[`exot::utilities::enum_operations_enabled< Advice >`](#structexot_1_1utilities_1_1enum__operations__enabled_3_01Advice_01_4) | Overload of [enum_operations_enabled](#structexot_1_1utilities_1_1enum__operations__enabled) for Advice.
`struct `[`exot::utilities::Evicter`](#structexot_1_1utilities_1_1Evicter) | Accesses memory with specific patterns.
`struct `[`exot::utilities::file_reader`](#structexot_1_1utilities_1_1file__reader) | File reader with raw data access.
`struct `[`exot::utilities::has_input_interface`](#structexot_1_1utilities_1_1has__input__interface) | 
`struct `[`exot::utilities::has_input_interface< T, std::enable_if_t< is_consumer_v< T > > >`](#structexot_1_1utilities_1_1has__input__interface_3_01T_00_01std_1_1enable__if__t_3_01is__consumer__v_3_01T_01_4_01_4_01_4) | 
`struct `[`exot::utilities::has_output_interface`](#structexot_1_1utilities_1_1has__output__interface) | 
`struct `[`exot::utilities::has_output_interface< T, std::enable_if_t< is_producer_v< T > > >`](#structexot_1_1utilities_1_1has__output__interface_3_01T_00_01std_1_1enable__if__t_3_01is__producer__v_3_01T_01_4_01_4_01_4) | 
`struct `[`exot::utilities::has_process_function`](#structexot_1_1utilities_1_1has__process__function) | Type trait to determine if a class has a void(void) process() function.
`struct `[`exot::utilities::has_process_function< T, std::void_t< decltype(std::declval< std::decay_t< T >>().process())> >`](#structexot_1_1utilities_1_1has__process__function_3_01T_00_01std_1_1void__t_3_01decltype_07std_15714445d2f036b890de6592dc077f2b9) | 
`struct `[`exot::utilities::has_push_back`](#structexot_1_1utilities_1_1has__push__back) | Type trait which determines if a type is CopyInsertable and can be appended to.
`struct `[`exot::utilities::has_push_back< T, std::void_t< decltype(std::declval< T >().push_back(typename T::value_type{}))> >`](#structexot_1_1utilities_1_1has__push__back_3_01T_00_01std_1_1void__t_3_01decltype_07std_1_1declv5245f06c998069f2b126f35ea4f1fef8) | 
`struct `[`exot::utilities::is_character`](#structexot_1_1utilities_1_1is__character) | Type trait for character types.
`struct `[`exot::utilities::is_character< CharT, std::enable_if_t<(std::is_same_v< CharT, char >\|\|std::is_same_v< CharT, wchar_t >\|\|std::is_same_v< CharT, char16_t >\|\|std::is_same_v< CharT, char32_t >)> >`](#structexot_1_1utilities_1_1is__character_3_01CharT_00_01std_1_1enable__if__t_3_07std_1_1is__samea306beda790e2dccea23e978b6b79ee0) | 
`struct `[`exot::utilities::is_clock`](#structexot_1_1utilities_1_1is__clock) | Is the given type a std::chrono-like clock?
`struct `[`exot::utilities::is_clock< T, std::void_t< typename std::decay_t< T >::duration, typename std::decay_t< T >::rep, typename std::decay_t< T >::period, typename std::decay_t< T >::time_point, decltype(std::declval< std::decay_t< T >>().now())> >`](#structexot_1_1utilities_1_1is__clock_3_01T_00_01std_1_1void__t_3_01typename_01std_1_1decay__t_3_e4312b160b30e888b9564072ef7a908d) | 
`struct `[`exot::utilities::is_comparable`](#structexot_1_1utilities_1_1is__comparable) | Determines if a type is EqualityComparable and LessThanComparable.
`struct `[`exot::utilities::is_configurable`](#structexot_1_1utilities_1_1is__configurable) | Type trait which determines whether a type has a settings member type, and component and type member functions.
`struct `[`exot::utilities::is_configurable< T, std::enable_if_t< std::is_base_of_v< configurable_base, T > >, std::void_t< decltype(std::declval< std::decay_t< T >>().name()), decltype(std::declval< std::decay_t< T >>().configure())> >`](#structexot_1_1utilities_1_1is__configurable_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base_29e243e6329f5cb3d89eefd6d165e578) | 
`struct `[`exot::utilities::is_const_iterable`](#structexot_1_1utilities_1_1is__const__iterable) | Type trait which determines if a type is const-iterable.
`struct `[`exot::utilities::is_const_iterable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::const_iterator, decltype(std::declval< std::decay_t< T >>().cbegin()), decltype(std::declval< std::decay_t< T >>().cend())> >`](#structexot_1_1utilities_1_1is__const__iterable_3_01T_00_01std_1_1void__t_3_01typename_01std_1_1df2b1a8b7e568c8baec7a29fd9373020b) | 
`struct `[`exot::utilities::is_consumer`](#structexot_1_1utilities_1_1is__consumer) | 
`struct `[`exot::utilities::is_consumer< T, std::enable_if_t< std::is_base_of_v< exot::framework::TConsumer, std::decay_t< T > > > >`](#structexot_1_1utilities_1_1is__consumer_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base__of_4cc47bb6ffdd352ab2ae390537498f65) | 
`struct `[`exot::utilities::is_duration`](#structexot_1_1utilities_1_1is__duration) | Is the given type a std::chrono::duration?
`struct `[`exot::utilities::is_duration< std::chrono::duration< Rep, Period > >`](#structexot_1_1utilities_1_1is__duration_3_01std_1_1chrono_1_1duration_3_01Rep_00_01Period_01_4_01_4) | 
`struct `[`exot::utilities::is_equality_comparable`](#structexot_1_1utilities_1_1is__equality__comparable) | Determines if a type is EqualityComparable (named C++ req.)
`struct `[`exot::utilities::is_equality_comparable< T, std::void_t< decltype(std::declval< T & >()==std::declval< T & >())> >`](#structexot_1_1utilities_1_1is__equality__comparable_3_01T_00_01std_1_1void__t_3_01decltype_07std741eb9cbc46959fd05b2c5296c943610) | 
`struct `[`exot::utilities::is_iterable`](#structexot_1_1utilities_1_1is__iterable) | Type trait which determines if a type satisfies the properties of an iterable type.
`struct `[`exot::utilities::is_iterable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::iterator, decltype(std::declval< std::decay_t< T >>().begin()), decltype(std::declval< std::decay_t< T >>().end())> >`](#structexot_1_1utilities_1_1is__iterable_3_01T_00_01std_1_1void__t_3_01typename_01std_1_1decay__tb7d62002acd7b51abd734987be219ca4) | Valid if the template parameter `std::void_t` is well formed, when all types given to it as parameters are present/valid.
`struct `[`exot::utilities::is_iterable_and_clearable`](#structexot_1_1utilities_1_1is__iterable__and__clearable) | Type trait which determines if a type satisfies the properties of an iterable type.
`struct `[`exot::utilities::is_iterable_and_clearable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::iterator, decltype(std::declval< std::decay_t< T >>().begin()), decltype(std::declval< std::decay_t< T >>().end()), decltype(std::declval< std::decay_t< T >>().clear())> >`](#structexot_1_1utilities_1_1is__iterable__and__clearable_3_01T_00_01std_1_1void__t_3_01typename_050ce63234dcb9bb5a017b625b133f838) | Valid if the template parameter `std::void_t` is well formed, when all types given to it as parameters are present/valid.
`struct `[`exot::utilities::is_lessthan_comparable`](#structexot_1_1utilities_1_1is__lessthan__comparable) | Determines if a type is LessThanComparable (named C++ req.)
`struct `[`exot::utilities::is_location_accessible`](#structexot_1_1utilities_1_1is__location__accessible) | Type trait which determines if a type has some Container facilities: size, and element-wise access.
`struct `[`exot::utilities::is_location_accessible< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::size_type, decltype(std::declval< T & >().size()), decltype(std::declval< T & >().at(std::declval< typename std::decay_t< T >::size_type >())), decltype(std::declval< T & >().operator[](std::declval< typename std::decay_t< T >::size_type >()))> >`](#structexot_1_1utilities_1_1is__location__accessible_3_01T_00_01std_1_1void__t_3_01typename_01stdc23dc2382d8586e616661b7b71cb9e82) | 
`struct `[`exot::utilities::is_processor`](#structexot_1_1utilities_1_1is__processor) | 
`struct `[`exot::utilities::is_processor< T, std::enable_if_t< std::is_base_of_v< exot::framework::TProcessor, std::decay_t< T > > > >`](#structexot_1_1utilities_1_1is__processor_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base__of77a8540757d0529a68b61d517a22c5e9) | 
`struct `[`exot::utilities::is_producer`](#structexot_1_1utilities_1_1is__producer) | 
`struct `[`exot::utilities::is_producer< T, std::enable_if_t< std::is_base_of_v< exot::framework::TProducer, std::decay_t< T > > > >`](#structexot_1_1utilities_1_1is__producer_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base__of_8d362f8e5e2f19671fbf4255181bbfa7) | 
`struct `[`exot::utilities::is_readable_from_stream`](#structexot_1_1utilities_1_1is__readable__from__stream) | Determines if a type can be read from an input stream (>>)
`struct `[`exot::utilities::is_tuple`](#structexot_1_1utilities_1_1is__tuple) | Type trait which determines if a type is a std::tuple specialisation.
`struct `[`exot::utilities::is_vector`](#structexot_1_1utilities_1_1is__vector) | Type trait which determines if a type is a std::vector.
`struct `[`exot::utilities::is_vector< std::vector< T, Alloc > >`](#structexot_1_1utilities_1_1is__vector_3_01std_1_1vector_3_01T_00_01Alloc_01_4_01_4) | 
`struct `[`exot::utilities::is_writable_to_stream`](#structexot_1_1utilities_1_1is__writable__to__stream) | Determines if a type can be writen to an output stream (<<)
`struct `[`exot::utilities::larger_of`](#structexot_1_1utilities_1_1larger__of) | Provides the larger of two types as a member type.
`struct `[`exot::utilities::serialised_time_source_t`](#structexot_1_1utilities_1_1serialised__time__source__t) | The serialised time source.
`struct `[`exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Atomic, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1Atomic_698eae7c0917b008e4caa1328f2ffd2d) | 
`struct `[`exot::utilities::serialised_time_source_t< Clock, TimingFenceType::None, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1None_006e00cd1f6bbe1b1d274ee9ee7889b31e) | 
`struct `[`exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Strong, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1Strong_cc90ab1ce53116f24e12bd9aac03e588) | 
`struct `[`exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Weak, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1Weak_007b5d15101215c09ff525420bfdae3094) | 
`struct `[`exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Atomic, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1Atomi0498789b2379c2f53a2ab6c49a3760cf) | 
`struct `[`exot::utilities::serialised_time_source_t< Counter, TimingFenceType::None, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1None_88139d913dbff5f95c56df9630082c61) | 
`struct `[`exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Strong, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1Stron5b6ac524cec58840d8831f8e6f69c421) | 
`struct `[`exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Weak, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >`](#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1Weak_2f687a55c658b3eff2f41dc6d2c82658) | 
`struct `[`exot::utilities::smaller_of`](#structexot_1_1utilities_1_1smaller__of) | Provides the smaller of two types as a member type.
`struct `[`exot::utilities::synchronised_t`](#structexot_1_1utilities_1_1synchronised__t) | Synchronised type wrapper.
`struct `[`exot::utilities::ThreadTraits`](#structexot_1_1utilities_1_1ThreadTraits) | A class that holds static methods to set thread properties.
`struct `[`exot::utilities::time_source_t`](#structexot_1_1utilities_1_1time__source__t) | The time source type, a clock or a counter.
`struct `[`exot::utilities::time_source_t< TimingSourceType::HardwarePerformanceCounter >`](#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1HardwarePerformanceCounter_01_4) | 
`struct `[`exot::utilities::time_source_t< TimingSourceType::MonotonicClock >`](#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1MonotonicClock_01_4) | 
`struct `[`exot::utilities::time_source_t< TimingSourceType::MonotonicCounter >`](#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1MonotonicCounter_01_4) | 
`struct `[`exot::utilities::time_source_t< TimingSourceType::SoftwarePerformanceCounter >`](#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1SoftwarePerformanceCounter_01_4) | 
`struct `[`exot::utilities::time_source_t< TimingSourceType::SteadyClock >`](#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1SteadyClock_01_4) | 
`struct `[`exot::utilities::is_lessthan_comparable< T, std::void_t< decltype(std::declval< T & >()< std::declval< T & >())> >`](#structexot_1_1utilities_1_1is__lessthan__comparable_3_01T_00_01std_1_1void__t_3_01decltype_07stdb0a26240cd828af3e2e34ed0f506bb5e) | 
`struct `[`exot::utilities::is_comparable< T, std::void_t< decltype(std::declval< T & >()==std::declval< T & >()), decltype(std::declval< T & >()< std::declval< T & >())> >`](#structexot_1_1utilities_1_1is__comparable_3_01T_00_01std_1_1void__t_3_01decltype_07std_1_1declva291e77fcf2c740f79acc0eb5ffe579f8) | 

## Members

#### `enum `[`Advice`](#namespaceexot_1_1utilities_1aeb849b1782b1d461631e01564e44895e) {#namespaceexot_1_1utilities_1aeb849b1782b1d461631e01564e44895e}

 Values                         | Descriptions                                
--------------------------------|---------------------------------------------
normal            | 
random            | 
sequential            | 
willneed            | 
dontneed            | 
remove            | 
dontfork            | 
dofork            | 
hwpoison            | 
mergeable            | 
unmergeable            | 
hugepage            | 
nohugepage            | 
dontdump            | 
dodump            | 
free            | 
keeponfork            | 

Enumeration for madvice(2) advice bits.

Prevents invalid use and establishes strong types.

#### `enum `[`Symlinks`](#namespaceexot_1_1utilities_1af10d2366991225e19e246b49a00cd410) {#namespaceexot_1_1utilities_1af10d2366991225e19e246b49a00cd410}

 Values                         | Descriptions                                
--------------------------------|---------------------------------------------
Follow            | 
Ignore            | 

alias for struct stat

Enum to indicate whether symlinks are to be followed or ignored.

#### `enum `[`SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7) {#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7}

 Values                         | Descriptions                                
--------------------------------|---------------------------------------------
Other            | 
Fifo            | 
RoundRobin            | 
Deadline            | 
Batch            | 
Idle            | 

A typed enum class which holds implementation-specific scheduling policy values.

An enum is used so that users do not need to include the <sched.h> header, and also to make the function calls more explicit, since functions would take the same type `int` in direct succession.

#### `enum `[`TimingFenceType`](#namespaceexot_1_1utilities_1a8d8408c73eabacb3009c90f7a2105381) {#namespaceexot_1_1utilities_1a8d8408c73eabacb3009c90f7a2105381}

 Values                         | Descriptions                                
--------------------------------|---------------------------------------------
Atomic            | 
Weak            | 
Strong            | 
None            | 

Enumeration for timing serialisation type.

#### `enum `[`TimingSourceType`](#namespaceexot_1_1utilities_1a7d9886836faa99c4a301171fc4eeb3db) {#namespaceexot_1_1utilities_1a7d9886836faa99c4a301171fc4eeb3db}

 Values                         | Descriptions                                
--------------------------------|---------------------------------------------
SteadyClock            | 
MonotonicCounter            | 
MonotonicClock            | 
TimeStampCounter            | 
HardwarePerformanceCounter            | 
SoftwarePerformanceCounter            | 

Enumeration for timing source.

#### `public inline constexpr bool `[`is_valid_alignment`](#namespaceexot_1_1utilities_1aa3c7dfac11730d87c342d67c453f1dc4)`(std::size_t value) noexcept` {#namespaceexot_1_1utilities_1aa3c7dfac11730d87c342d67c453f1dc4}

Determines if a number is a valid alignment.

#### Parameters
* `value` The alignment

#### Returns
True if a value is a power of 2, False otherwise.

#### `public template<>`  <br/>`constexpr auto `[`make_aligned`](#namespaceexot_1_1utilities_1af6ee47359aa2fd798e3f390ec5fce62d)`(T t)` {#namespaceexot_1_1utilities_1af6ee47359aa2fd798e3f390ec5fce62d}

Makes an aligned version of a value.

#### Parameters
* `t` The value to make aligned

#### Parameters
* `A` The alignment 

* `T` The value type

#### Returns
An aligned value

#### `public inline void `[`advise`](#namespaceexot_1_1utilities_1a1747b84aa0322121fd40e3946f468760)`(void * address,std::size_t length,`[`Advice`](#namespaceexot_1_1utilities_1aeb849b1782b1d461631e01564e44895e)` advice)` {#namespaceexot_1_1utilities_1a1747b84aa0322121fd40e3946f468760}

Advises the kernel about how a memory range is used.

#### Parameters
* `address` The address 

* `length` The length 

* `advice` The advice

#### `public template<>`  <br/>`bool `[`operator!=`](#namespaceexot_1_1utilities_1a9e2691dc0d0c208cc9703ea3e544e390)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T1, Al1 > & lhs,const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T2, Al2 > & rhs) noexcept` {#namespaceexot_1_1utilities_1a9e2691dc0d0c208cc9703ea3e544e390}

Checks if allocators are not the same.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `T1` The lhs value type 

* `Al1` The lhs alignment 

* `T2` The rhs value type 

* `Al2` The rhs alignment

#### Returns
Always false (stateless allocator)

#### `public template<>`  <br/>`bool `[`operator==`](#namespaceexot_1_1utilities_1a52206fbc9fefec829f8c84a2902258fd)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T1, Al1 > & lhs,const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< T2, Al2 > & rhs) noexcept` {#namespaceexot_1_1utilities_1a52206fbc9fefec829f8c84a2902258fd}

Checks if allocators are the same.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `T1` The lhs value type 

* `Al1` The lhs alignment 

* `T2` The rhs value type 

* `Al2` The rhs alignment

#### Returns
Always true (stateless allocator)

#### `public template<>`  <br/>`inline constexpr `[`larger_of_t`](#namespaceexot_1_1utilities_1ae76699e649bf5d3f7609eae176d5ec74)`< T1, T2 > `[`make_bitmask`](#namespaceexot_1_1utilities_1a806d2668c57cd5ef52b7651ade4f5d6b)`(T1 lower_bit,T2 upper_bit)` {#namespaceexot_1_1utilities_1a806d2668c57cd5ef52b7651ade4f5d6b}

Makes a bitmask.

Some of the bit manipulation functions use the compiler's builtins, which should be available for both GCC and LLVM compilers.

The function sets bits from lower_bit to upper_bit, e.g. a call `make_bitmask(2L, 5ULL)` will produce a number `0b11100`. Thanks to templating, the function should work for many types without implicit casting, and provides overflow checks for the shift operations.

#### Parameters
* `lower_bit` The lower set bit of the bitmask 

* `upper_bit` The upper set bit of the bitmask

#### Parameters
* `T1` Type of lower_bit 

* `T2` Type of upper_bit 

* `<unnamed>` Template helper to enable the function only for integral types

#### Returns
A bitmask with bits set from lower_bit to upper_bit

#### `public template<>`  <br/>`inline constexpr T1 `[`extract_with_bitmask`](#namespaceexot_1_1utilities_1a00ab7c9901b343a5e52bdb791eac474f)`(T1 value,T2 bitmask)` {#namespaceexot_1_1utilities_1a00ab7c9901b343a5e52bdb791eac474f}

Extracts a value by applying a bitmask.

The function applies the bitmask, and shifts the value by the number of trailing zeros in the bitmask. For example, by calling `extract_with_bitmask(0b11011001, 0b111100)`, we obtain the result `0b1011`, i.e. `0b11011001 & 0b00111100`, which is `0b00101100`, then shifted by 2, to produce `0b1011`.

#### Parameters
* `value` The value 

* `bitmask` The bitmask

#### Parameters
* `T1` The type of the value 

* `T2` The type of the bitmask 

* `<unnamed>` Template helper to enable the function only for integral types

#### Returns
The extracted value, i.e. the shifted bitmasked original value

#### `public template<>`  <br/>`inline constexpr T1 `[`extract_bit_range`](#namespaceexot_1_1utilities_1aca68266a2d0b633df88a90f19690276f)`(T1 value,T2 lower_bit,T3 upper_bit)` {#namespaceexot_1_1utilities_1aca68266a2d0b633df88a90f19690276f}

#### `public template<>`  <br/>`inline constexpr void `[`set_bit`](#namespaceexot_1_1utilities_1ae3eb6767de882a6fb7264e2952f969d4)`(T & value,B bit)` {#namespaceexot_1_1utilities_1ae3eb6767de882a6fb7264e2952f969d4}

#### `public template<>`  <br/>`inline constexpr void `[`set_bits`](#namespaceexot_1_1utilities_1a263432f9cd5c8807e5c061c257e793e2)`(T & value,Bs... bits)` {#namespaceexot_1_1utilities_1a263432f9cd5c8807e5c061c257e793e2}

#### `public template<>`  <br/>`inline constexpr void `[`set_bit_range`](#namespaceexot_1_1utilities_1a88ae6d6d37f474ce6aea5f6af133423a)`(T1 & value,T2 lower_bit,T3 upper_bit)` {#namespaceexot_1_1utilities_1a88ae6d6d37f474ce6aea5f6af133423a}

#### `public template<>`  <br/>`inline constexpr T `[`get_bit`](#namespaceexot_1_1utilities_1ad4e8a57bb27e1512cba249f9d5d30ac2)`(T value,B bit)` {#namespaceexot_1_1utilities_1ad4e8a57bb27e1512cba249f9d5d30ac2}

#### `public template<>`  <br/>`inline constexpr void `[`clear_bit`](#namespaceexot_1_1utilities_1a523396f307d880fdfb9e21820e43c4dc)`(T & value,B bit)` {#namespaceexot_1_1utilities_1a523396f307d880fdfb9e21820e43c4dc}

#### `public template<>`  <br/>`inline constexpr void `[`clear_bits`](#namespaceexot_1_1utilities_1a391b9d75257c02d549309612b2f758e5)`(T & value,Bs... bits)` {#namespaceexot_1_1utilities_1a391b9d75257c02d549309612b2f758e5}

#### `public template<>`  <br/>`inline constexpr void `[`clear_bit_range`](#namespaceexot_1_1utilities_1a36b25f5854164b878e0b0c65a310401a)`(T1 & value,T2 lower_bit,T3 upper_bit)` {#namespaceexot_1_1utilities_1a36b25f5854164b878e0b0c65a310401a}

#### `public template<>`  <br/>`inline constexpr void `[`toggle_bit`](#namespaceexot_1_1utilities_1a0cd350985f3dbf589e72e244210ff85a)`(T & value,B bit)` {#namespaceexot_1_1utilities_1a0cd350985f3dbf589e72e244210ff85a}

#### `public template<>`  <br/>`inline constexpr void `[`toggle_bits`](#namespaceexot_1_1utilities_1a08b4796d7930eea139c419c8c1acbe5b)`(T & value,Bs... bits)` {#namespaceexot_1_1utilities_1a08b4796d7930eea139c419c8c1acbe5b}

#### `public template<>`  <br/>`inline constexpr void `[`toggle_bit_range`](#namespaceexot_1_1utilities_1a5f1e588169ef4c28046edb9baa20383a)`(T1 & value,T2 lower_bit,T3 upper_bit)` {#namespaceexot_1_1utilities_1a5f1e588169ef4c28046edb9baa20383a}

#### `public template<>`  <br/>`inline bool `[`test_bit`](#namespaceexot_1_1utilities_1a449e921e92b712b70ce24ffb41c981d9)`(T value,B bit)` {#namespaceexot_1_1utilities_1a449e921e92b712b70ce24ffb41c981d9}

#### `public template<>`  <br/>`inline bool `[`test_bits`](#namespaceexot_1_1utilities_1af5b6d1cf86efb84c23609e485b5bd983)`(T value,Bs... bits)` {#namespaceexot_1_1utilities_1af5b6d1cf86efb84c23609e485b5bd983}

#### `public template<>`  <br/>`inline constexpr bool `[`test_bit_range`](#namespaceexot_1_1utilities_1ae83329519e9b7f7f2ad77e78d827e4d9)`(T1 value,T2 lower_bit,T3 upper_bit)` {#namespaceexot_1_1utilities_1ae83329519e9b7f7f2ad77e78d827e4d9}

#### `public template<>`  <br/>`inline constexpr int `[`hamming_weight`](#namespaceexot_1_1utilities_1a4242685386b06d67c7ff7490b629bf92)`(T value)` {#namespaceexot_1_1utilities_1a4242685386b06d67c7ff7490b629bf92}

Return the hamming weight of a number, the count of bits set to 1.

#### Parameters
* `value` The evaluated value

#### Parameters
* `T` The type of the value 

* `<unnamed>` Template helper

#### Returns
The count of individual bits set to 1

#### `public template<>`  <br/>`inline constexpr int `[`parity`](#namespaceexot_1_1utilities_1ad990f69f531a2f2ccbc7128316f518e6)`(T value)` {#namespaceexot_1_1utilities_1ad990f69f531a2f2ccbc7128316f518e6}

Return the parity of the value (evenness/oddness of an integer)

#### Parameters
* `value` The evaluated value

#### Parameters
* `T` The type of the value 

* `<unnamed>` Template helper

#### Returns
The parity of the value

#### `public template<>`  <br/>`inline constexpr int `[`trailing_zero_bits`](#namespaceexot_1_1utilities_1a8771ead3f27e092a8efaddc480931fd3)`(T value)` {#namespaceexot_1_1utilities_1a8771ead3f27e092a8efaddc480931fd3}

Gets the number of trailing zero bits in an unsigned integer.

Takes care of the case when 0 is given, for which BSR or BSF operations are undefined. In such case the number of digits in the type T is returned.

#### Parameters
* `value` The evaluated value

#### Parameters
* `T` The type of the value 

* `<unnamed>` Template helper

#### Returns
The number of trailing bits in the value

#### `public template<>`  <br/>`inline constexpr int `[`leading_zero_bits`](#namespaceexot_1_1utilities_1a304a1ca5cd9b82296e553d6e3ffc292b)`(T value)` {#namespaceexot_1_1utilities_1a304a1ca5cd9b82296e553d6e3ffc292b}

Gets the number of leading zero bits in an unsigned integer.

Takes care of the case when 0 is given, for which BSR or BSF operations are undefined. In such case the number of digits in the type T is returned.

#### Parameters
* `value` The evaluated value

#### Parameters
* `T` The type of the value 

* `<unnamed>` Template helper

#### Returns
The number of leading bits in the value

#### `public template<>`  <br/>`inline constexpr std::size_t `[`next_set_bit`](#namespaceexot_1_1utilities_1aa47525741009521ecf68fb28530796b8)`(T value,std::size_t bit)` {#namespaceexot_1_1utilities_1aa47525741009521ecf68fb28530796b8}

Gets the position of the next set bit in an unsigned integer.

If the 'bit' value is greater than the number of digits in the type T, the function returns the latter, and sets errno to EDOM.

The function can be use to loop through set bits in a number, like so:

```cpp for (auto i = next_set_bit(value, 0); i < std::numeric_limits<decltype(value)>::digits; i = next_set_bit(value, i + 1)); ```

#### Parameters
* `value` The value 

* `bit` The bit from which the testing is performed

#### Parameters
* `T` The type of the value 

* `<unnamed>` Template helper

#### Returns
The bit position of the next set bit

#### `public template<>`  <br/>`inline constexpr void `[`loop_through_set_bits`](#namespaceexot_1_1utilities_1a28b7ffc68ae5561ee6d75a2b415eed6a)`(T value,F && callable)` {#namespaceexot_1_1utilities_1a28b7ffc68ae5561ee6d75a2b415eed6a}

Executes a callable with indeces of set bits in a value.

#### Parameters
* `value` The value 

* `callable` The callable, must be invocable as void(size_t)

#### Parameters
* `T` The type of the value 

* `F` The callable type 

* `<unnamed>` Template helper

#### `public template<>`  <br/>`inline void `[`set_json`](#namespaceexot_1_1utilities_1a47e792a1b7a5e283d2a19c2d05bda20f)`(const `[`JsonConfig`](#classexot_1_1utilities_1_1JsonConfig)` & config,Ts &&... ts)` {#namespaceexot_1_1utilities_1a47e792a1b7a5e283d2a19c2d05bda20f}

Sets the JSON file in multiple configurables.

#### Parameters
* `config` The [JsonConfig](#classexot_1_1utilities_1_1JsonConfig) object 

* `ts` The configurables

#### Parameters
* `Ts` The types of the configurables

#### `public template<>`  <br/>`inline void `[`configure`](#namespaceexot_1_1utilities_1ab0ab2922d2b0aba8a69b9398ce9074b5)`(const `[`JsonConfig`](#classexot_1_1utilities_1_1JsonConfig)` & config,Ts &&... ts)` {#namespaceexot_1_1utilities_1ab0ab2922d2b0aba8a69b9398ce9074b5}

Sets the JSON file in multiple configurables and configures them.

#### Parameters
* `config` The [JsonConfig](#classexot_1_1utilities_1_1JsonConfig) object 

* `ts` The configurables

#### Parameters
* `Ts` The types of the configurables

#### `public template<>`  <br/>`inline void `[`get_from_json_to`](#namespaceexot_1_1utilities_1a60cbd26352cb380d79a6ae33103f67ac)`(const nlohmann::json & json,K key,T & ref)` {#namespaceexot_1_1utilities_1a60cbd26352cb380d79a6ae33103f67ac}

Attempts to assign a value from a json object to a referenced variable, using the provided key.

#### Parameters
* `json` The json object 

* `key` The key 

* `ref` The reference to data

#### Parameters
* `T` The type of data 

* `<unnamed>` Template helper

#### `public template<>`  <br/>`inline void `[`get_from_json_to`](#namespaceexot_1_1utilities_1aa66a50d55ab96801ce1932144fb0df1a)`(const nlohmann::json & json,const char * key,T & ref)` {#namespaceexot_1_1utilities_1aa66a50d55ab96801ce1932144fb0df1a}

Temporary partial specialisation for get_from_json_to and const char* key.

#### `public template<>`  <br/>`inline void `[`get_from_json_to`](#namespaceexot_1_1utilities_1a5ecba66ecbe970436b4e4dffe5ca086d)`(const nlohmann::json & json,const nlohmann::json::json_pointer & key,T & ref)` {#namespaceexot_1_1utilities_1a5ecba66ecbe970436b4e4dffe5ca086d}

Temporary partial specialisation for get_from_json_to and a JSON pointer.

#### `public template<>`  <br/>`inline void `[`set_json`](#namespaceexot_1_1utilities_1a44565970841862f6fb492ffe40e3329a)`(U json,Ts &&... ts)` {#namespaceexot_1_1utilities_1a44565970841862f6fb492ffe40e3329a}

Sets the JSON object in configurables.

#### Parameters
* `json` The json 

* `ts` The configurables

#### Parameters
* `U` The type in which the json object is provided 

* `Ts` The types of the configurables

#### `public template<>`  <br/>`inline void `[`configure`](#namespaceexot_1_1utilities_1a5d264c66da8e5b3e2b1d83a66de240cb)`(U json,Ts &&... ts)` {#namespaceexot_1_1utilities_1a5d264c66da8e5b3e2b1d83a66de240cb}

Sets the JSON object in configurables and configures them.

#### Parameters
* `json` The json 

* `ts` The configurables

#### Parameters
* `U` The type in which the json object is provided 

* `Ts` The types of the configurables

#### `public template<>`  <br/>`inline void `[`set_json`](#namespaceexot_1_1utilities_1a1cf2c2e7f520d7130a0820a06cb944c5)`(nlohmann::json::const_reference root,Ts &&... ts)` {#namespaceexot_1_1utilities_1a1cf2c2e7f520d7130a0820a06cb944c5}

Sets the JSON file in multiple configurables.

#### Parameters
* `root` The root JSON 

* `ts` The configurables

#### Parameters
* `Ts` The types of the configurables

#### `public template<>`  <br/>`inline void `[`only_configure`](#namespaceexot_1_1utilities_1af64d0b3e99802cf1386ba81b9a360308)`(Ts &&... ts)` {#namespaceexot_1_1utilities_1af64d0b3e99802cf1386ba81b9a360308}

Configures multiple configurables.

#### Parameters
* `ts` The configurables

#### Parameters
* `Ts` The types of the configurables

#### `public template<>`  <br/>`inline void `[`configure`](#namespaceexot_1_1utilities_1ab22a772f5cf0b07b0d2b58a3bbd28dd4)`(nlohmann::json::const_reference root,Ts &&... ts)` {#namespaceexot_1_1utilities_1ab22a772f5cf0b07b0d2b58a3bbd28dd4}

Sets the JSON file in multiple configurables and configures them.

#### Parameters
* `root` The root JSON 

* `ts` The configurables

#### Parameters
* `Ts` The types of the configurables

#### `public template<>`  <br/>`void `[`sort_and_deduplicate`](#namespaceexot_1_1utilities_1a66ed3e57b283b6b861f4fe75a54f2a82)`(std::vector< T > & vector)` {#namespaceexot_1_1utilities_1a66ed3e57b283b6b861f4fe75a54f2a82}

Sort and deduplicate a vector of comparable elements.

> Todo: Move to a more general header file

#### Parameters
* `vector` The vector

#### Parameters
* `T` The sorted and deduplicated vector

#### `public void `[`bootstrap_cores`](#namespaceexot_1_1utilities_1a31beaa3c9014604091575a5d8f2b401c)`(std::vector< unsigned > & cores)` {#namespaceexot_1_1utilities_1a31beaa3c9014604091575a5d8f2b401c}

Bootstrap a vector of cores.

Checks hardware concurrency, initialises the vector if empty, and checks if any of the specified cores are out of range.

#### Parameters
* `cores` The vector with core numbers

#### `public template<>`  <br/>`std::string `[`generate_header`](#namespaceexot_1_1utilities_1a976ffe281ad359722fd9172d753c38f7)`(Ts &&... ts)` {#namespaceexot_1_1utilities_1a976ffe281ad359722fd9172d753c38f7}

Generate a header for application logging purposes.

#### Parameters
* `ts` Values to supply to the header, exactly 4 have to be provided. 1: module, 2: variable, 3: dimension, 4: unit.

#### Parameters
* `Ts` Types of values, see static_assert's for compatibility

#### Returns
A string with a formatted header

#### `public template<>`  <br/>`inline constexpr Enum `[`operator|`](#namespaceexot_1_1utilities_1aa828d3adbee98a5783f6c1fc8a292ebf)`(Enum lhs,Enum rhs)` {#namespaceexot_1_1utilities_1aa828d3adbee98a5783f6c1fc8a292ebf}

Bit-wise "or" operator overload.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper

#### Returns
The or'ed enum result

#### `public template<>`  <br/>`inline constexpr Enum & `[`operator|=`](#namespaceexot_1_1utilities_1ae81202afa3a7e88b1cbf2dd01cc89d62)`(Enum lhs,Enum rhs)` {#namespaceexot_1_1utilities_1ae81202afa3a7e88b1cbf2dd01cc89d62}

Bit-wise "or" assignment operator overload.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper

#### Returns
A reference to the or'ed lhs enum

#### `public template<>`  <br/>`inline constexpr Enum `[`operator&`](#namespaceexot_1_1utilities_1aafcf79262999e838b7de7ecf70a591f7)`(Enum lhs,Enum rhs)` {#namespaceexot_1_1utilities_1aafcf79262999e838b7de7ecf70a591f7}

Bit-wise "and" operator overload.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper

#### Returns
The and'ed enum

#### `public template<>`  <br/>`inline constexpr Enum & `[`operator&=`](#namespaceexot_1_1utilities_1a60408208f1761967016cade61a77d7d7)`(Enum lhs,Enum rhs)` {#namespaceexot_1_1utilities_1a60408208f1761967016cade61a77d7d7}

Bit-wise "and" assignment operator overload.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper

#### Returns
A reference to the and'ed lhs enum

#### `public template<>`  <br/>`inline constexpr Enum `[`operator^`](#namespaceexot_1_1utilities_1ab1ec359abf8aff73e508ea436f913e76)`(Enum lhs,Enum rhs)` {#namespaceexot_1_1utilities_1ab1ec359abf8aff73e508ea436f913e76}

Bit-wise "xor" operator overload.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper

#### Returns
The xor'ed enum

#### `public template<>`  <br/>`inline constexpr Enum & `[`operator^=`](#namespaceexot_1_1utilities_1a3e638c61523d7f6161e3b05d8d79a68f)`(Enum lhs,Enum rhs)` {#namespaceexot_1_1utilities_1a3e638c61523d7f6161e3b05d8d79a68f}

Bit-wise "xor" assignment operator overload.

#### Parameters
* `lhs` The left hand side 

* `rhs` The right hand side

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper

#### Returns
A reference to the xor'ed lhs enum

#### `public template<>`  <br/>`inline constexpr Enum & `[`operator~`](#namespaceexot_1_1utilities_1a16c508b10990b586d09fbd9842002db5)`(Enum e)` {#namespaceexot_1_1utilities_1a16c508b10990b586d09fbd9842002db5}

Bit-wise "not" operator overload.

#### Parameters
* `e` The enum

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper

#### Returns
The not'ed enum

#### `public bool `[`is_readable`](#namespaceexot_1_1utilities_1a491635ae7135842c9e2089fd47ef2224)`(const std::string & path)` {#namespaceexot_1_1utilities_1a491635ae7135842c9e2089fd47ef2224}

Checks if a provided file can be read.

#### Parameters
* `path` The path

#### Returns
True if readable, False otherwise.

#### `public bool `[`exists`](#namespaceexot_1_1utilities_1ab8e2431393863eb11908c87faf4a9de7)`(const std::string & path)` {#namespaceexot_1_1utilities_1ab8e2431393863eb11908c87faf4a9de7}

Checks if a provided path exists.

#### Parameters
* `path` The path

#### Returns
True if exists, False otherwise.

#### `public bool `[`is_directory`](#namespaceexot_1_1utilities_1a5a74a2aab967c8bc33eb83e54cbd481d)`(const std::string & path)` {#namespaceexot_1_1utilities_1a5a74a2aab967c8bc33eb83e54cbd481d}

Determines if a path is a directory.

#### Parameters
* `path` The path

#### Returns
True if directory, False otherwise.

#### `public auto `[`get_stat`](#namespaceexot_1_1utilities_1a77c8233e3606b643e4de8f29c0d9b879)`(const std::string & path)` {#namespaceexot_1_1utilities_1a77c8233e3606b643e4de8f29c0d9b879}

Gets the sys/stat.h 'stat' struct for a path.

#### Parameters
* `path` The path

#### Returns
The stat if successful, nullopt otherwise.

#### `public bool `[`all_readable`](#namespaceexot_1_1utilities_1adda329da05ce7089e8484b20532f5b4c)`(const std::vector< std::string > & paths)` {#namespaceexot_1_1utilities_1adda329da05ce7089e8484b20532f5b4c}

Checks if all provided files can be accessed.

#### Parameters
* `paths` A vector of path names

#### Returns
True if all are readable

#### `public bool `[`is_empty`](#namespaceexot_1_1utilities_1aedaa579544f1d723acc13dab064ff63f)`(const std::string & file_path)` {#namespaceexot_1_1utilities_1aedaa579544f1d723acc13dab064ff63f}

Determines if a file is empty.

#### Parameters
* `file_path` The file path

#### Returns
True if empty, False otherwise.

#### `public std::vector< std::string > `[`remove_unreadable`](#namespaceexot_1_1utilities_1a9bd010519c0d52f3b96680890c58d06b)`(std::vector< std::string > & paths)` {#namespaceexot_1_1utilities_1a9bd010519c0d52f3b96680890c58d06b}

Removes unreadable files from a vector of paths.

#### Parameters
* `paths` The vector of path names

#### Returns
A vector of paths that have been removed, can be empty.

#### `public template<>`  <br/>`inline auto `[`get_value_from_file`](#namespaceexot_1_1utilities_1a644204a275e889767cf49d257a11ebc8)`(const std::string & path)` {#namespaceexot_1_1utilities_1a644204a275e889767cf49d257a11ebc8}

Get a value of certain type from file.

The function template relies on input stream overloads being present for the type defined in template parameters.

#### Parameters
* `path` The path

#### Parameters
* `To` The desired type

#### Returns
The value from file if readable, nullopt otherwise.

#### `public auto `[`get_long_string_value_from_file`](#namespaceexot_1_1utilities_1a7aa994ed10f5501386883214ec2a5016)`(const std::string & path)` {#namespaceexot_1_1utilities_1a7aa994ed10f5501386883214ec2a5016}

Gets the long string value from file.

#### Parameters
* `path` The path as a const string reference

#### Returns
The long string value from file if readable, nullopt otherwise.

#### `public auto `[`get_string_value_from_file`](#namespaceexot_1_1utilities_1a97b91fa578b36e75133e7c502c36ce00)`(const std::string & path)` {#namespaceexot_1_1utilities_1a97b91fa578b36e75133e7c502c36ce00}

Gets a string value from a file.

#### Parameters
* `path` The path as a const string reference

#### Returns
The string value from file if readable, nullopt otherwise.

#### `public template<>`  <br/>`std::vector< std::basic_string< CharT > > `[`split_string`](#namespaceexot_1_1utilities_1aa9d044c4fc5fd2457d2c9b49b42c561f)`(const std::basic_string< CharT > & string,CharT delimiter)` {#namespaceexot_1_1utilities_1aa9d044c4fc5fd2457d2c9b49b42c561f}

Splits a string using a delimeter.

#### Parameters
* `string` The string 

* `delimiter` The delimiter

#### Parameters
* `CharT` Character type (e.g. char, wchar_t)

#### Returns
A vector with the tokenized string

#### `public template<>`  <br/>`std::basic_string< CharT > `[`join_strings`](#namespaceexot_1_1utilities_1aeda506b3b1f0ba00e4048ba861a60c7d)`(const std::vector< std::basic_string< CharT >> & strings,CharT delimiter)` {#namespaceexot_1_1utilities_1aeda506b3b1f0ba00e4048ba861a60c7d}

Joins a vector of strings into a single delimited string.

#### Parameters
* `strings` The strings 

* `delimiter` The delimiter

#### Parameters
* `CharT` Character type used by basic_string

#### Returns
The joined string

#### `public template<>`  <br/>`std::string `[`wrap`](#namespaceexot_1_1utilities_1a359b7f814215bdd7682e2fef260fe2ee)`(const std::basic_string< CharT > & to_wrap,size_t width,size_t indent)` {#namespaceexot_1_1utilities_1a359b7f814215bdd7682e2fef260fe2ee}

Wraps a string to a desired number of columns.

#### Parameters
* `to_wrap` String to wrap 

* `width` The width of the column in characters 

* `indent` The indentation of the next lines

#### Returns
The wrapped string

#### `public template<>`  <br/>`std::string `[`indent`](#namespaceexot_1_1utilities_1a9cfad0c2e6f19b757f89803686ea5dfa)`(const std::basic_string< CharT > & to_indent,size_t indent,bool wrap)` {#namespaceexot_1_1utilities_1a9cfad0c2e6f19b757f89803686ea5dfa}

#### `public template<>`  <br/>`std::string `[`trim_string`](#namespaceexot_1_1utilities_1a455fb3ce629172a9fb900b7b7080a606)`(const std::basic_string< CharT > & to_trim,const std::basic_string< CharT > & trim_characters)` {#namespaceexot_1_1utilities_1a455fb3ce629172a9fb900b7b7080a606}

Trim characters at front and back of the string, mostly for whitespace.

#### Parameters
* `to_trim` The string to trim 

* `trim_characters` A string with characters to be trimmed

#### Parameters
* `CharT` Character type use by basic_string 

* `_` Template helper

#### Returns
A trimmed string

#### `public template<>`  <br/>`std::string `[`trim_string`](#namespaceexot_1_1utilities_1a84005e89e742a3913b1d379d7b4ce296)`(const std::basic_string< CharT > & to_trim,const CharT * trim_characters)` {#namespaceexot_1_1utilities_1a84005e89e742a3913b1d379d7b4ce296}

#### `public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1aa7a63337367d561f61e7b26947d867e4)`(const std::basic_string< CharT > & to_collapse,const std::basic_string< CharT > & fill_characters,const std::basic_string< CharT > & collapse_characters)` {#namespaceexot_1_1utilities_1aa7a63337367d561f61e7b26947d867e4}

Collapse characters present in a string, preferably whitespace.

#### Parameters
* `to_collapse` The string to collapse 

* `collapse_characters` A string with characters to

#### Parameters
* `CharT` The character tupe 

* `_` Template helper

#### Returns
The collapsed string

#### `public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1a30f0a0f656d2d68769fa808c35f892ce)`(const std::basic_string< CharT > & to_collapse,const std::basic_string< CharT > & fill_characters,const CharT * collapse_characters)` {#namespaceexot_1_1utilities_1a30f0a0f656d2d68769fa808c35f892ce}

#### `public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1a49cd2d9c3e1268f3add063a98a328a8d)`(const std::basic_string< CharT > & to_collapse,const CharT * fill_characters,const CharT * collapse_characters)` {#namespaceexot_1_1utilities_1a49cd2d9c3e1268f3add063a98a328a8d}

#### `public template<>`  <br/>`std::string `[`collapse_string`](#namespaceexot_1_1utilities_1aa9de72e523edcf6af82f7a1700277370)`(const std::basic_string< CharT > & to_collapse,const CharT * fill_characters,const std::basic_string< CharT > & collapse_characters)` {#namespaceexot_1_1utilities_1aa9de72e523edcf6af82f7a1700277370}

#### `public inline unsigned `[`extract_number`](#namespaceexot_1_1utilities_1aa9e40ef7dea6fc0fa3d96b5d804df61d)`(const std::string & string)` {#namespaceexot_1_1utilities_1aa9e40ef7dea6fc0fa3d96b5d804df61d}

Extract the first occurence of a positive number from a string.

#### Parameters
* `string` The string

#### Returns
The extracted number

#### `public inline std::vector< unsigned > `[`extract_numbers`](#namespaceexot_1_1utilities_1afd0c8ca7867d0eeb862d5fb44db51f2f)`(const std::string & in)` {#namespaceexot_1_1utilities_1afd0c8ca7867d0eeb862d5fb44db51f2f}

Extract the all occurences of positive numbers from a string.

#### Parameters
* `in` The string

#### Returns
The extracted number

#### `public inline unsigned `[`read_hex_value`](#namespaceexot_1_1utilities_1af38ee523f89c67ca601e3fadc3b24184)`(const std::string & string)` {#namespaceexot_1_1utilities_1af38ee523f89c67ca601e3fadc3b24184}

Helper function for obtaining an unsigned number from a hexadecimal string notation, also without the leading '0x'.

#### Parameters
* `str` The string

#### Returns
The converted value

#### `public template<>`  <br/>`std::string `[`ratio_to_string`](#namespaceexot_1_1utilities_1a273a667f73f461eeef7c8384386d3780)`(std::ratio< Num, Den > ratio) noexcept` {#namespaceexot_1_1utilities_1a273a667f73f461eeef7c8384386d3780}

Get a string description of a ratio.

The SI unit prefixes of {yocto, zepto, zetta, yotta} cannot yet be represented in any of the standard built-in types (value exceeds size limit).

#### Parameters
* `ratio` The ratio

#### Parameters
* `Num` Value of the numerator 

* `Den` Value of the denominator

#### Returns
A string with the SI prefix

#### `public template<>`  <br/>`std::string `[`duration_unit`](#namespaceexot_1_1utilities_1a77629eee17cffdca74b6506eca965292)`(std::chrono::duration< Rep, Period >)` {#namespaceexot_1_1utilities_1a77629eee17cffdca74b6506eca965292}

Get a unit prefix of a duration period.

#### Parameters
* `duration` The duration

#### Parameters
* `Rep` Type used to store the duration 

* `Period` The duration period

#### Returns
Time unit string with prefixes

#### `public template<>`  <br/>`std::string `[`duration_to_string`](#namespaceexot_1_1utilities_1a0026502c0e48f91e8c28b91b379413fd)`(std::chrono::duration< Rep, Period > duration)` {#namespaceexot_1_1utilities_1a0026502c0e48f91e8c28b91b379413fd}

Print a duration with its unit.

#### Parameters
* `duration` The duration

#### Parameters
* `Rep` Type used to store the duration 

* `Period` The duration period

#### Returns
String with the duration and its unit with prefixes

#### `public template<>`  <br/>`constexpr void `[`const_for`](#namespaceexot_1_1utilities_1ab1f46f0d798d093a4221294da0f717e6)`(Callable && func)` {#namespaceexot_1_1utilities_1ab1f46f0d798d093a4221294da0f717e6}

A compile-time for-loop.

Uses the helper above to generate a sequence of `std::size_t` integers from Begin to End, invokes the callable object with the constexpr index, e.g. `std::integral_constant<unsigned long, 0ul>` on a 64-bit architecture. If a lambda is provided, the call will be to an anonymous class' `operator() const`. Functions provided to the static for-loop should also be constexpr.

#### Parameters
* `func` A callable object

#### Parameters
* `Begin` First sequence number (similar to the first parameter in a `for` loop declaration) 

* `End` Last sequence number (similar to the second parameter in a `for` loop declaration, increment is implied) 

* `Callable` A callable type

#### `public template<>`  <br/>`constexpr void `[`for_each`](#namespaceexot_1_1utilities_1ab52416714fd0b45168ed6ff929eb8a08)`(std::tuple< Ts... > && tuple,Callable && func)` {#namespaceexot_1_1utilities_1ab52416714fd0b45168ed6ff929eb8a08}

Apply a function to each tuple element.

#### Parameters
* `tuple` The tuple 

* `func` A callable object

#### Parameters
* `Callable` A callable type 

* `Ts` Individual tuple types

#### `public template<>`  <br/>`auto `[`tail`](#namespaceexot_1_1utilities_1ae63930670c418e9393f98f648a078fe6)`(std::tuple< Ts... > && value)` {#namespaceexot_1_1utilities_1ae63930670c418e9393f98f648a078fe6}

#### `public template<>`  <br/>`auto `[`zip`](#namespaceexot_1_1utilities_1a84d5c61305b2449309cec8b5079cd064)`(T && t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a84d5c61305b2449309cec8b5079cd064}

Zips multiple tuples together.

#### Parameters
* `T` The first tuple type 

* `Ts` The other tuples' types 

#### Parameters
* `t` The first tuple 

* `ts` The other tuples 

#### Returns
The zipped tuples

#### `public template<>`  <br/>`auto `[`zip_fwd`](#namespaceexot_1_1utilities_1a05ec94d6ca96f43b118e455e0939412e)`(T && t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a05ec94d6ca96f43b118e455e0939412e}

Zips multiple tuples together by forwarding values.

#### Parameters
* `T` The first tuple type 

* `Ts` The other tuples' types 

#### Parameters
* `t` The first tuple 

* `ts` The other tuples 

#### Returns
The zipped tuples

#### `public template<>`  <br/>`auto `[`mean_and_deviation`](#namespaceexot_1_1utilities_1a7a69efeca7d0189affb1f54dd9be6fa0)`(const std::vector< T > & input)` {#namespaceexot_1_1utilities_1a7a69efeca7d0189affb1f54dd9be6fa0}

Calculates the mean and standard deviation of values in a container.

#### Parameters
* `input` The input container

#### Parameters
* `T` The value type 

* `<unnamed>` Template helper

#### Returns
The mean and deviation as an array of doubles

#### `public template<>`  <br/>`constexpr auto `[`slice`](#namespaceexot_1_1utilities_1a6fd0e700dde7e74da01a061a886afa8a)`(const T & container,std::size_t lower,std::size_t upper)` {#namespaceexot_1_1utilities_1a6fd0e700dde7e74da01a061a886afa8a}

Gets a slice of an interable container.

#### Parameters
* `container` The container 

* `lower` The lower index 

* `upper` The upper index

#### Parameters
* `T` The type of the container 

* `<unnamed>` Template helper

#### Returns
The slice, reversed if lower < upper

#### `public template<>`  <br/>`constexpr auto `[`percentile`](#namespaceexot_1_1utilities_1a10667f9bac01143ca54a86176397fe80)`(T container,double value)` {#namespaceexot_1_1utilities_1a10667f9bac01143ca54a86176397fe80}

Gets a percentile of values in a container.

Only arithmetic value types are supported.

#### Parameters
* `container` The container 

* `value` The percentile in range (0, 1)

#### Parameters
* `T` The container type 

* `<unnamed>` Template helper

#### Returns
The percentile value of elements in the container.

#### `public template<>`  <br/>`constexpr auto `[`percentile_sort_in_place`](#namespaceexot_1_1utilities_1a8598f09e55e3d217c7982c97437a60e2)`(T & container,double value)` {#namespaceexot_1_1utilities_1a8598f09e55e3d217c7982c97437a60e2}

Gets a percentile of values in a container, sorting it in place.

Only arithmetic value types are supported. The side effect is that the input container will become sorted.

#### Parameters
* `container` The container 

* `value` The percentile in range (0, 1)

#### Parameters
* `T` The container type 

* `<unnamed>` Template helper

#### Returns
The percentile value of elements in the container.

#### `public template<>`  <br/>`constexpr auto `[`percentile_range`](#namespaceexot_1_1utilities_1a4e56e0c83a1ad5af8d3aefdf9f4fd0d8)`(T container,double lower,double upper)` {#namespaceexot_1_1utilities_1a4e56e0c83a1ad5af8d3aefdf9f4fd0d8}

Gets a slice of a container in percentile limits.

#### Parameters
* `container` The container 

* `lower` The lower percentile in range (0, 1] 

* `upper` The upper percentile in range (0, 1]

#### Parameters
* `T` The container type 

* `<unnamed>` Template helper

#### Returns
A slice of the container within limits, reversed if lower > upper

#### `public template<>`  <br/>`inline constexpr bool `[`is_power_of_2`](#namespaceexot_1_1utilities_1a3d8f91f6680b5f0b83721f29e991730d)`(T value) noexcept` {#namespaceexot_1_1utilities_1a3d8f91f6680b5f0b83721f29e991730d}

Determines if power of 2.

#### Parameters
* `value` The value

#### Parameters
* `T` The type of the value (unsigned integral) 

* `<unnamed>` Template helper

#### Returns
True if power of 2, False otherwise.

#### `public template<>`  <br/>`inline constexpr bool `[`is_one_of`](#namespaceexot_1_1utilities_1abe6e879f78cf2de7b6ade50435865aa9)`(T && t,Ts &&... ts)` {#namespaceexot_1_1utilities_1abe6e879f78cf2de7b6ade50435865aa9}

Determines if a value is within a set of other values.

#### Parameters
* `t` The value to compare 

* `ts` The set of values to compare against

#### Parameters
* `T` The type of the value to compare 

* `Ts` The types of the values to compare against 

* `<unnamed>` Template helper which determines if all decayed types are the same

#### Returns
True if t is one of ts, False otherwise.

#### `public template<>`  <br/>`inline constexpr bool `[`is_none_of`](#namespaceexot_1_1utilities_1a77f933ffe1d47f86ac78fda77b69b1c1)`(T && t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a77f933ffe1d47f86ac78fda77b69b1c1}

Determines if a value is not in a set of other values.

#### Parameters
* `t` The value to compare 

* `ts` The set of values to compare against

#### Parameters
* `T` The type of the value to compare 

* `Ts` The types of the values to compare against 

* `<unnamed>` Template helper which determines if all decayed types are the same

#### Returns
True if t isn't one of ts, False otherwise.

#### `public template<>`  <br/>`auto `[`contains`](#namespaceexot_1_1utilities_1a8eafda304811f6c707dc0ee5274eb662)`(typename T::value_type v,const T & container)` {#namespaceexot_1_1utilities_1a8eafda304811f6c707dc0ee5274eb662}

Check if a container contains an element.

The provided type T must conform to the '[is_iterable](#structexot_1_1utilities_1_1is__iterable)' type trait, the value type is obtained from a member type/alias 'value_type'.

#### Parameters
* `v` The value to check 

* `container` The container

#### Parameters
* `T` The type of the container 

* `<unnamed>` Template helper

#### Returns
True if found, false otherwise.

#### `public template<>`  <br/>`constexpr bool `[`is_greater`](#namespaceexot_1_1utilities_1ad1fa959c908c36f621995c4494ec31bc)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1ad1fa959c908c36f621995c4494ec31bc}

#### `public template<>`  <br/>`constexpr bool `[`is_greater_or_equal`](#namespaceexot_1_1utilities_1ad489950b8b27f67148f287dcab4fe250)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1ad489950b8b27f67148f287dcab4fe250}

#### `public template<>`  <br/>`constexpr bool `[`assert_is_greater`](#namespaceexot_1_1utilities_1ac24a007dffab9f51aeac19b5c5efa73b)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1ac24a007dffab9f51aeac19b5c5efa73b}

#### `public template<>`  <br/>`constexpr bool `[`assert_is_greater_or_equal`](#namespaceexot_1_1utilities_1a90ddafe9fa6a46e8df903bf2af721078)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a90ddafe9fa6a46e8df903bf2af721078}

#### `public template<>`  <br/>`constexpr bool `[`is_smaller`](#namespaceexot_1_1utilities_1a28436e4afc9d6961696eb460dbfb5aa3)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a28436e4afc9d6961696eb460dbfb5aa3}

#### `public template<>`  <br/>`constexpr bool `[`is_smaller_or_equal`](#namespaceexot_1_1utilities_1a3789a4a1fddd3bf13df62b1811f5dfe5)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a3789a4a1fddd3bf13df62b1811f5dfe5}

#### `public template<>`  <br/>`constexpr bool `[`assert_is_smaller`](#namespaceexot_1_1utilities_1a486588c53a98389088eb84b58f905456)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a486588c53a98389088eb84b58f905456}

#### `public template<>`  <br/>`constexpr bool `[`assert_is_smaller_or_equal`](#namespaceexot_1_1utilities_1a6b3e316a8dc7e2bf98b00d9de4a7173c)`(T t,Ts &&... ts)` {#namespaceexot_1_1utilities_1a6b3e316a8dc7e2bf98b00d9de4a7173c}

#### `public template<>`  <br/>`inline  `[`__attribute__`](#namespaceexot_1_1utilities_1a97737d9b68d855784bed53f42770e971)`((always_inline)) const` {#namespaceexot_1_1utilities_1a97737d9b68d855784bed53f42770e971}

Helper to prevent the compiler from optimising a variable.

#### Parameters
* `var` The const reference to the variable

#### Parameters
* `T` The type of the variable

#### Parameters
* `var` The reference to the variable

#### Parameters
* `T` The type of the variable

#### `public template<>`  <br/>`inline  `[`__attribute__`](#namespaceexot_1_1utilities_1aabb32788e9721b5cb61fc214df923082)`((always_inline))` {#namespaceexot_1_1utilities_1aabb32788e9721b5cb61fc214df923082}

Alias for US spelling of 'optimise'.

#### `public template<>`  <br/>`constexpr bool `[`is_constexpr`](#namespaceexot_1_1utilities_1aaffdbcf77206e7cbc043659c60e966cb)`(Ts &&... ts)` {#namespaceexot_1_1utilities_1aaffdbcf77206e7cbc043659c60e966cb}

Determines if values or function returns are constexpr.

Cannot be used on functions with signatures void(...).

#### Parameters
* `ts` The values

#### Parameters
* `Ts` The value types

#### Returns
True if all are constexpr, False otherwise.

#### `public template<>`  <br/>`std::istream & `[`operator>>`](#namespaceexot_1_1utilities_1a667d1c0a022b6dcdecfa51f4d0851c42)`(std::basic_istream< CharT, CharTraitsT > & stream,std::chrono::duration< Rep, Period > & duration)` {#namespaceexot_1_1utilities_1a667d1c0a022b6dcdecfa51f4d0851c42}

Input stream operator overload for reading durations.

#### Parameters
* `stream` The input stream 

* `duration` The duration object

#### Parameters
* `CharT` Character type used by the stream 

* `CharTraitsT` Character traits used by the stream 

* `Rep` The underlying type used by the duration 

* `Period` The underlying period type used by the duration

#### Returns
The duration with assigned value

#### `public template<>`  <br/>`std::tuple< Current, Rest... > `[`read_tuple`](#namespaceexot_1_1utilities_1aa715562a4af5f4f3c8cf106103f62f80)`(std::basic_istream< CharT, CharTraitsT > & stream)` {#namespaceexot_1_1utilities_1aa715562a4af5f4f3c8cf106103f62f80}

Reads a tuple from an istream.

#### Parameters
* `stream` The input stream

#### Parameters
* `CharT` Character type used by the stream 

* `CharTraitsT` Character traits used by the stream 

* `Current` The current tuple element type 

* `Rest` The types of the other tuple elements

#### Returns
A tuple with read values

#### `public inline constexpr unsigned long long `[`operator""_KiB`](#namespaceexot_1_1utilities_1a14c6657637682b32516d099b05d36589)`(unsigned long long v)` {#namespaceexot_1_1utilities_1a14c6657637682b32516d099b05d36589}

Converts a kibibytes value to bytes.

#### Parameters
* `v` The value in kibibytes

#### Returns
The value in bytes

#### `public inline constexpr unsigned long long `[`operator""_MiB`](#namespaceexot_1_1utilities_1a354deb2ddbbfccf7a5ae4cf6e64e89bc)`(unsigned long long v)` {#namespaceexot_1_1utilities_1a354deb2ddbbfccf7a5ae4cf6e64e89bc}

Converts a mebibytes value to bytes.

#### Parameters
* `v` The value in mebibytes

#### Returns
The value in bytes

#### `public inline constexpr unsigned long long `[`operator""_GiB`](#namespaceexot_1_1utilities_1ab4aeb268b9065a03b6addcbeb0c8b428)`(unsigned long long v)` {#namespaceexot_1_1utilities_1ab4aeb268b9065a03b6addcbeb0c8b428}

Converts a gibibytes value to bytes.

#### Parameters
* `v` The value in gibibytes

#### Returns
The value in bytes

#### `public void `[`append_to_filename`](#namespaceexot_1_1utilities_1ab813a8b40662932691338ca0d76ba853)`(std::string & file_path,const std::string & to_append)` {#namespaceexot_1_1utilities_1ab813a8b40662932691338ca0d76ba853}

Appends a string to the filename.

#### Parameters
* `file_path` The file path 

* `to_append` To string to append

#### `public void `[`append_timestamp_to_filename`](#namespaceexot_1_1utilities_1a2e5799143f95382615e0ae8bf83d8148)`(std::string & file_path)` {#namespaceexot_1_1utilities_1a2e5799143f95382615e0ae8bf83d8148}

Appends a timestamp to a filename.

#### Parameters
* `file_path` The path to the file

#### `public template<>`  <br/>`auto `[`cli_wrapper`](#namespaceexot_1_1utilities_1a7e78562cba2977aa14bcd76022fb56f8)`(int argc,char ** argv)` {#namespaceexot_1_1utilities_1a7e78562cba2977aa14bcd76022fb56f8}

Provides a cli main wrapper for typical applications.

#### Parameters
* `Components` The component types 

#### Parameters
* `argc` The argc from main 

* `argv` The argv from main 

#### Returns
Return code [0, 1]

#### `public std::optional< std::string > `[`get_kernel_version`](#namespaceexot_1_1utilities_1a7f0409a861baf75342dc109450e6ec52)`()` {#namespaceexot_1_1utilities_1a7f0409a861baf75342dc109450e6ec52}

Gets the kernel version.

#### Returns
The kernel version. Nullopt if unsuccessful.

#### `public std::vector< std::string > `[`get_cpuinfo_keys`](#namespaceexot_1_1utilities_1a5443629202666c4e38fc291772276060)`()` {#namespaceexot_1_1utilities_1a5443629202666c4e38fc291772276060}

Gets all the available cpuinfo keys.

#### Returns
The cpuinfo keys.

#### `public std::optional< std::map< std::string, std::string > > `[`get_cpuinfo_as_map`](#namespaceexot_1_1utilities_1ae23243ed6562e9275a85641e1c6dc850)`(unsigned cpu)` {#namespaceexot_1_1utilities_1ae23243ed6562e9275a85641e1c6dc850}

Gets the cpuinfo key-value pairs as a map for a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The cpuinfo as map. Empty if unsuccessful.

#### `public std::vector< std::map< std::string, std::string > > `[`get_complete_cpuinfo_as_map_array`](#namespaceexot_1_1utilities_1a57323b071d00e7590fa45600c6493af0)`()` {#namespaceexot_1_1utilities_1a57323b071d00e7590fa45600c6493af0}

Gets the complete cpuinfo as map array.

#### Returns
The complete cpuinfo as map array.

#### `public std::optional< std::string > `[`get_cpuinfo_value`](#namespaceexot_1_1utilities_1a05f9a1a524fa6a26c04edf4562ba78fa)`(unsigned cpu,const std::string & key)` {#namespaceexot_1_1utilities_1a05f9a1a524fa6a26c04edf4562ba78fa}

Gets the cpuinfo value for a given key for a specific cpu.

#### Parameters
* `cpu` The cpu 

* `key` The key

#### Returns
The cpuinfo value. Nullopt if unsuccessful.

#### `public std::vector< std::string > `[`get_cpuinfo_values`](#namespaceexot_1_1utilities_1a48d6bab28cb922fe34b999e7c8786f13)`(const std::string & key)` {#namespaceexot_1_1utilities_1a48d6bab28cb922fe34b999e7c8786f13}

Gets the cpuinfo values for a given key for all cpus.

#### Parameters
* `key` The key

#### Returns
The cpuinfo values. Empty if unsuccessful.

#### `public unsigned `[`get_cpu_count`](#namespaceexot_1_1utilities_1a33adcc8cddf191ac571f017eb9813463)`()` {#namespaceexot_1_1utilities_1a33adcc8cddf191ac571f017eb9813463}

Gets the cpu count.

#### Returns
The cpu count.

#### `public unsigned `[`get_thread_count`](#namespaceexot_1_1utilities_1a72a1a329722d10c1b7e551c7126ea9a5)`()` {#namespaceexot_1_1utilities_1a72a1a329722d10c1b7e551c7126ea9a5}

Gets the thread count.

#### Returns
The thread count.

#### `public unsigned `[`get_core_count`](#namespaceexot_1_1utilities_1acae1bd2eec2587e6c4bf940074c652e8)`()` {#namespaceexot_1_1utilities_1acae1bd2eec2587e6c4bf940074c652e8}

Gets the core count.

#### Returns
The core count.

#### `public unsigned `[`get_socket_count`](#namespaceexot_1_1utilities_1a109d7bb24dc351cbed069d29153e4a0a)`()` {#namespaceexot_1_1utilities_1a109d7bb24dc351cbed069d29153e4a0a}

Gets the socket count.

#### Returns
The socket count.

#### `public unsigned `[`get_thread_per_core`](#namespaceexot_1_1utilities_1a41e006e0e988cbe914c546f58a9944de)`()` {#namespaceexot_1_1utilities_1a41e006e0e988cbe914c546f58a9944de}

Gets the thread per core. Derived from get_thread_count and get_core_count.

#### Returns
The thread per core.

#### `public unsigned `[`get_core_per_socket`](#namespaceexot_1_1utilities_1a9ae0e678ad5db0c2f8c14514c1c864e8)`()` {#namespaceexot_1_1utilities_1a9ae0e678ad5db0c2f8c14514c1c864e8}

Gets the core per socket. Derived from get_core_count and get_socket_count.

#### Returns
The core per socket.

#### `public const char * `[`get_target_architecture`](#namespaceexot_1_1utilities_1ad32fed5bbf796015525711cff54ba814)`() noexcept` {#namespaceexot_1_1utilities_1ad32fed5bbf796015525711cff54ba814}

Gets the target architecture. Returns a compile-time value.

#### Returns
The target architecture for which the binary was compiled.

#### `public std::optional< std::string > `[`get_cpu_vendor`](#namespaceexot_1_1utilities_1a4d564f211ea602094b44648f1e669ab4)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a4d564f211ea602094b44648f1e669ab4}

Gets the cpu vendor of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The cpu vendor. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::string > `[`get_cpu_model`](#namespaceexot_1_1utilities_1af38813feffb718987234632834a80b19)`(unsigned cpu)` {#namespaceexot_1_1utilities_1af38813feffb718987234632834a80b19}

Gets the cpu model of a specific cpu.

For x86_64 chips the model will be reported as: name: "{}", family: {}, model: {}, stepping: {} For ARM-based chips the model will be reported as: arch: {}, variant: {}, part: "{}", revision: {}

#### Parameters
* `cpu` The cpu

#### Returns
The cpu model. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::vector< std::string > > `[`get_unique_cpu_models`](#namespaceexot_1_1utilities_1ab200e0cd33037c72afefed357806106a)`()` {#namespaceexot_1_1utilities_1ab200e0cd33037c72afefed357806106a}

Gets all unique cpu models and their associated cpus.

#### Returns
A vector with unique cpu models and the associated cpu list. Nullopt if unsuccessful.

#### `public std::optional< std::string > `[`get_cpu_flags`](#namespaceexot_1_1utilities_1ad85d5a65320180280b0370acaad5e6b9)`(unsigned cpu)` {#namespaceexot_1_1utilities_1ad85d5a65320180280b0370acaad5e6b9}

Gets the cpu flags of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The cpu flags. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::vector< std::string > > `[`get_cpu_flags_array`](#namespaceexot_1_1utilities_1a4736afc3ee64f00045d0b6747f7b7722)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a4736afc3ee64f00045d0b6747f7b7722}

Gets the cpu flags as an array for a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The cpu flags array. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::string > `[`get_scaling_governor`](#namespaceexot_1_1utilities_1a1208e4b3b1783b5e826b75f9970ad82b)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a1208e4b3b1783b5e826b75f9970ad82b}

Gets the scaling governor of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The scaling governor. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::array< unsigned long, 2 > > `[`get_cpu_frequencies`](#namespaceexot_1_1utilities_1a50b92d34ed4543b5dbe35c6dcd927ae5)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a50b92d34ed4543b5dbe35c6dcd927ae5}

Gets the min and max cpu frequencies of a specific cpu. The frequencies are given in Hz.

#### Parameters
* `cpu` The cpu

#### Returns
The cpu frequencies. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned long > `[`get_min_cpu_frequency`](#namespaceexot_1_1utilities_1ae3f06867e9c4f2051024d1056ec1c558)`(unsigned cpu)` {#namespaceexot_1_1utilities_1ae3f06867e9c4f2051024d1056ec1c558}

Gets the minimum cpu frequency of a specific cpu. The frequency is given in Hz.

#### Parameters
* `cpu` The cpu

#### Returns
The minimum cpu frequency. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned long > `[`get_max_cpu_frequency`](#namespaceexot_1_1utilities_1a88c6c940ac2585fdfa3b9298bf15e114)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a88c6c940ac2585fdfa3b9298bf15e114}

Gets the maximum cpu frequency of a specific cpu. The frequency is given in Hz.

#### Parameters
* `cpu` The cpu

#### Returns
The maximum cpu frequency. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::string `[`get_online_cpus`](#namespaceexot_1_1utilities_1abf6b4e44b578cbb1fd96535ea4296a91)`()` {#namespaceexot_1_1utilities_1abf6b4e44b578cbb1fd96535ea4296a91}

Gets the string representation of online cpus.

The string representation usually informs about a range of active cpus, e.g. in the form "0-7" for active cpus from 0 to 7.

#### Returns
The online cpus. An empty string if unsuccessful.

#### `public std::string `[`get_offline_cpus`](#namespaceexot_1_1utilities_1acc04c42127b5cc88c8af00a168a21a28)`()` {#namespaceexot_1_1utilities_1acc04c42127b5cc88c8af00a168a21a28}

Gets the string representation of offline cpus.

#### Returns
The offline cpus. An empty string if unsuccessful.

#### `public std::string `[`get_possible_cpus`](#namespaceexot_1_1utilities_1a6e4a71c86b85e5c902a89233b1175307)`()` {#namespaceexot_1_1utilities_1a6e4a71c86b85e5c902a89233b1175307}

Gets the string representation of possible cpus. Possible cpus are those that can be either brought online, or made offline.

#### Returns
The possible cpus. An empty string if unsuccessful.

#### `public std::vector< bool > `[`get_online_cpus_array`](#namespaceexot_1_1utilities_1a56331ec82c793b3502577d9ae71e0dd7)`()` {#namespaceexot_1_1utilities_1a56331ec82c793b3502577d9ae71e0dd7}

Gets the online cpus array.

#### Returns
The online cpus array. Empty if unsuccessful.

#### `public bool `[`is_cpu_online`](#namespaceexot_1_1utilities_1a02d352f68375595a85bce88ce8b006fe)`(unsigned int cpu)` {#namespaceexot_1_1utilities_1a02d352f68375595a85bce88ce8b006fe}

Determines if a cpu online.

#### Parameters
* `cpu` The cpu

#### Returns
True if cpu online, False otherwise. Also false for non-existent cpus.

#### `public std::optional< std::string > `[`get_topology_value`](#namespaceexot_1_1utilities_1a6dbb1392597134a70349e5c7ad0c93bd)`(unsigned cpu,const std::string & key)` {#namespaceexot_1_1utilities_1a6dbb1392597134a70349e5c7ad0c93bd}

Gets the topology value given a valid key for a specific cpu.

The possible keys are: "core_id", "core_siblings", "physical_package_id", "thread_siblings", "core_siblings_list", "thread_siblings_list", "book_id", "drawer_id", "book_siblings", "drawer_siblings".

#### Parameters
* `cpu` The cpu 

* `key` The key

#### Returns
The topology value. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned > `[`get_core_id`](#namespaceexot_1_1utilities_1a01f85d50c8c0b3364cb69215e52050df)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a01f85d50c8c0b3364cb69215e52050df}

Gets the core identifier of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The core identifier.Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned > `[`get_core_siblings`](#namespaceexot_1_1utilities_1af652e8d4b2409c25f4fd45d0e751e6d6)`(unsigned cpu)` {#namespaceexot_1_1utilities_1af652e8d4b2409c25f4fd45d0e751e6d6}

Gets the core siblings of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The core siblings. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::vector< unsigned > > `[`get_core_siblings_array`](#namespaceexot_1_1utilities_1a9d56a36fe956612ebfd7234c17bf957b)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a9d56a36fe956612ebfd7234c17bf957b}

Gets the core siblings as an array for a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The core siblings array. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned > `[`get_core_siblings_count`](#namespaceexot_1_1utilities_1a82a144e588b830b4ba9d9da554f716e8)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a82a144e588b830b4ba9d9da554f716e8}

Gets the core siblings count of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The core siblings count. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned > `[`get_physical_package_id`](#namespaceexot_1_1utilities_1a4652c75c01183d781a7ae46e1574dc14)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a4652c75c01183d781a7ae46e1574dc14}

Gets the physical package identifier of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The physical package identifier. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned > `[`get_thread_siblings`](#namespaceexot_1_1utilities_1a48c7f27068b7ac329ebb6f96dc2f3817)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a48c7f27068b7ac329ebb6f96dc2f3817}

Gets the thread siblings of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The thread siblings. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::vector< unsigned > > `[`get_thread_siblings_array`](#namespaceexot_1_1utilities_1a2f7e29ee4047c65a4a486281cf36e5ee)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a2f7e29ee4047c65a4a486281cf36e5ee}

Gets the thread siblings as an array for a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The thread siblings array. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< unsigned > `[`get_thread_siblings_count`](#namespaceexot_1_1utilities_1afac4a6b1c697925061c5cbfe90058384)`(unsigned cpu)` {#namespaceexot_1_1utilities_1afac4a6b1c697925061c5cbfe90058384}

Gets the thread siblings count of a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The thread siblings count. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::map< std::string, std::string > > `[`get_cpu_topology_map`](#namespaceexot_1_1utilities_1a507f3f9f6c8fb67bb3f54d6765b52598)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a507f3f9f6c8fb67bb3f54d6765b52598}

Gets the complete cpu topology as a map for a specific cpu.

#### Parameters
* `cpu` The cpu

#### Returns
The cpu topology map. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::optional< std::string > `[`get_cpu_topology`](#namespaceexot_1_1utilities_1aacddd09873395f1dee836823fb038e26)`(unsigned cpu)` {#namespaceexot_1_1utilities_1aacddd09873395f1dee836823fb038e26}

Gets the serialised cpu topology of a specific cpu as a string. The result is JSON-like formatted.

#### Parameters
* `cpu` The cpu

#### Returns
The cpu topology. Nullopt if unsuccessful, or if provided cpu does not exist.

#### `public std::vector< std::string > `[`get_complete_topology`](#namespaceexot_1_1utilities_1afa95e09e87c7959ff0188fac50a3c56d)`()` {#namespaceexot_1_1utilities_1afa95e09e87c7959ff0188fac50a3c56d}

Gets a description of the complete topology for all cpus. The result is JSON-like formatted.

#### Returns
The complete topology.

#### `public std::string `[`thread_info`](#namespaceexot_1_1utilities_1a5a4e5777ca7af7172e5c24ebeaef9db5)`()` {#namespaceexot_1_1utilities_1a5a4e5777ca7af7172e5c24ebeaef9db5}

Produce an info string containing information about the current thread.

#### Returns
A string containing the following: the id of the thread, the core on which the thread is running, the scheduling policy and priority

#### `public template<>`  <br/>`auto `[`timeit`](#namespaceexot_1_1utilities_1a2e5b48f12c277da73e7d0d79e5c4923a)`(Callable && callable,Args &&... args)` {#namespaceexot_1_1utilities_1a2e5b48f12c277da73e7d0d79e5c4923a}

Time the execution of a callable using timestamp counters.

Time the execution of a callable using any std::chrono-like clock.

#### Parameters
* `callable` The callable 

* `args` The arguments to the callable

#### Parameters
* `Counter` A TSC (must derive from TimeStampCounter) 

* `Callable` A callable type 

* `Args` Argument types to the callable 

* `<unnamed>` Template helper

#### Returns
The execution duration in TSC-specific units

#### Parameters
* `callable` The callable 

* `args` The arguments to the callable

#### Parameters
* `Clock` A Clock type, e.g. std::chrono::steady_clock 

* `Callable` A callable type 

* `Args` Argument types to the callable 

* `<unnamed>` Template helper

#### Returns
The execution duration as a duration, e.g. chrono::nanoseconds

#### `public template<>`  <br/>`inline static void `[`busysleep`](#namespaceexot_1_1utilities_1a8fb5c1ba9a5d78a7d465daf712f3142c)`(const std::chrono::duration< Rep, Period > & duration)` {#namespaceexot_1_1utilities_1a8fb5c1ba9a5d78a7d465daf712f3142c}

Busy sleep function, continuously checking if time has elapsed.

#### Parameters
* `duration` The sleep duration

#### Parameters
* `Rep` Underlying type used to represent the chrono duration 

* `Period` The ratio of the chrono duration

#### `public static std::tm `[`get_utc_time`](#namespaceexot_1_1utilities_1ac7298346d5ab650a39446d3de68f8ab3)`()` {#namespaceexot_1_1utilities_1ac7298346d5ab650a39446d3de68f8ab3}

Gets the UTC time as a C time struct.

#### Returns
The UTC time.

#### `public static std::tm `[`get_local_time`](#namespaceexot_1_1utilities_1ae56ada3ebdb04080b9b2d9abb1fd5345)`()` {#namespaceexot_1_1utilities_1ae56ada3ebdb04080b9b2d9abb1fd5345}

Gets the local time as a C time struct.

#### Returns
The local time.

#### `public template<>`  <br/>`inline auto `[`default_timing_facility`](#namespaceexot_1_1utilities_1af5a8018a7799ad8bcbd1441bcc20cd60)`(Args &&... args)` {#namespaceexot_1_1utilities_1af5a8018a7799ad8bcbd1441bcc20cd60}

The default timeing facility.

Wrapper of the "timeit" utility defined in <[exot/utilities/timing.h](#timing_8h)>

#### Parameters
* `Args` The forwarded arguments types 

#### Parameters
* `args` The forwarded arguments

#### Returns
The time measurement output in clock-specific type

#### `public template<>`  <br/>`constexpr auto `[`to_underlying_type`](#namespaceexot_1_1utilities_1ac9851a52cd02e651bd5e351e1eec0c19)`(T t)` {#namespaceexot_1_1utilities_1ac9851a52cd02e651bd5e351e1eec0c19}

Casts a type (e.g. scoped enum class) to its underlying type.

This function may come useful when used in conjunction with a typed enum, e.g. `enum class X : int {};`, for which the operation `to_underlying_type(X::x)` will return an `int`.

#### Parameters
* `t` An object to cast

#### Parameters
* `T` The type of the object

#### Returns
The object statically casted to its underlying type.

#### `public bool `[`is_cpu_online`](#namespaceexot_1_1utilities_1a80de8e36bf8759179c5b36343df3b884)`(unsigned cpu)` {#namespaceexot_1_1utilities_1a80de8e36bf8759179c5b36343df3b884}

# class `exot::utilities::Barrier` {#classexot_1_1utilities_1_1Barrier}

The barrier thread synchronisation primitive, also known as a randezvous point.

As each thread arrives at the barrier, it increments a counter, which states how many threads in total have reached the randezvous point. Threads lock on a mutex and are descheduled until the number of threads at the barrier is equal to the specified count. The thread last to reach the barrier unlocks the mutex and notifies all waiting threads.

The interface is modelled after barriers found in projects 'boost/thread' and 'boost/fiber'.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`Barrier`](#classexot_1_1utilities_1_1Barrier_1a421fbd9e2dda99ab79bdb444db674e16)`() = delete` | No default constructor.
`public  explicit `[`Barrier`](#classexot_1_1utilities_1_1Barrier_1abed1fc21841d4685f15cc3f22bb8681a)`(unsigned int count)` | Constructs the object with desired number of threads that need to reach the barrier.
`public  `[`~Barrier`](#classexot_1_1utilities_1_1Barrier_1a4ff9fb167d02207e82236d0b46585ef1)`() = default` | 
`public bool `[`wait`](#classexot_1_1utilities_1_1Barrier_1a03dae6ebdd2301ffc65bfde74c06eaf6)`()` | Waits until the number of threads at the barrier is equal to the desired count.
`public void `[`force_progress`](#classexot_1_1utilities_1_1Barrier_1ae0278fb6ab472a6cf2786ceb919c9583)`()` | Forces progress even if not all threads have reached the barrier.
`typedef `[`mutex_type`](#classexot_1_1utilities_1_1Barrier_1a76356b055966e01eb609c25a9bd391c7) | 
`typedef `[`cv_type`](#classexot_1_1utilities_1_1Barrier_1a6e9cd2fcf57669cea07b7ca2b19a24ff) | 

## Members

#### `public  `[`Barrier`](#classexot_1_1utilities_1_1Barrier_1a421fbd9e2dda99ab79bdb444db674e16)`() = delete` {#classexot_1_1utilities_1_1Barrier_1a421fbd9e2dda99ab79bdb444db674e16}

No default constructor.

#### `public  explicit `[`Barrier`](#classexot_1_1utilities_1_1Barrier_1abed1fc21841d4685f15cc3f22bb8681a)`(unsigned int count)` {#classexot_1_1utilities_1_1Barrier_1abed1fc21841d4685f15cc3f22bb8681a}

Constructs the object with desired number of threads that need to reach the barrier.

#### Parameters
* `count` The number of threads required for passing the barrier

#### `public  `[`~Barrier`](#classexot_1_1utilities_1_1Barrier_1a4ff9fb167d02207e82236d0b46585ef1)`() = default` {#classexot_1_1utilities_1_1Barrier_1a4ff9fb167d02207e82236d0b46585ef1}

#### `public bool `[`wait`](#classexot_1_1utilities_1_1Barrier_1a03dae6ebdd2301ffc65bfde74c06eaf6)`()` {#classexot_1_1utilities_1_1Barrier_1a03dae6ebdd2301ffc65bfde74c06eaf6}

Waits until the number of threads at the barrier is equal to the desired count.

#### Returns
Last thread to enter the barrier returns true, others return false.

#### `public void `[`force_progress`](#classexot_1_1utilities_1_1Barrier_1ae0278fb6ab472a6cf2786ceb919c9583)`()` {#classexot_1_1utilities_1_1Barrier_1ae0278fb6ab472a6cf2786ceb919c9583}

Forces progress even if not all threads have reached the barrier.

#### `typedef `[`mutex_type`](#classexot_1_1utilities_1_1Barrier_1a76356b055966e01eb609c25a9bd391c7) {#classexot_1_1utilities_1_1Barrier_1a76356b055966e01eb609c25a9bd391c7}

#### `typedef `[`cv_type`](#classexot_1_1utilities_1_1Barrier_1a6e9cd2fcf57669cea07b7ca2b19a24ff) {#classexot_1_1utilities_1_1Barrier_1a6e9cd2fcf57669cea07b7ca2b19a24ff}

# class `exot::utilities::CLI` {#classexot_1_1utilities_1_1CLI}

Class providing the command line interface.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public template<>`  <br/>`inline void `[`add_configurations`](#classexot_1_1utilities_1_1CLI_1a801c2c2f8443f0087ea25ccf94683d9f)`(const Configs &... config)` | Adds multiple configurations to the interface.
`public void `[`prepend_section`](#classexot_1_1utilities_1_1CLI_1a82aa2f99d6f51242ebe72058ddf733cf)`(const std::string & title,const std::string & content)` | Prepends a section to the help message.
`public void `[`append_section`](#classexot_1_1utilities_1_1CLI_1ad2147c937d33bdd91741b758d8fb4c66)`(const std::string & title,const std::string & content)` | Appends a section to the help message.
`public void `[`add_description`](#classexot_1_1utilities_1_1CLI_1ac9b259f77371ce704f014e1f9257b5e3)`(const std::string & description)` | Adds a description section to the help message.
`public void `[`add_example`](#classexot_1_1utilities_1_1CLI_1a000017d711c418c918ede732835837d0)`(const std::string & example)` | Adds an example section to the help message.
`public bool `[`parse`](#classexot_1_1utilities_1_1CLI_1ad6c92dd6520b8652b02fa256d1ad721b)`(int argc,char ** argv)` | Parses the command line arguments.
`public template<>`  <br/>`inline void `[`collect_descriptions`](#classexot_1_1utilities_1_1CLI_1a822f6f2c505cff659f4ed760da0256a3)`(Ts &&... ts)` | 

## Members

#### `public template<>`  <br/>`inline void `[`add_configurations`](#classexot_1_1utilities_1_1CLI_1a801c2c2f8443f0087ea25ccf94683d9f)`(const Configs &... config)` {#classexot_1_1utilities_1_1CLI_1a801c2c2f8443f0087ea25ccf94683d9f}

Adds multiple configurations to the interface.

#### Parameters
* `config` The individual configuration group

#### Parameters
* `Configs` Configuration groups

#### `public void `[`prepend_section`](#classexot_1_1utilities_1_1CLI_1a82aa2f99d6f51242ebe72058ddf733cf)`(const std::string & title,const std::string & content)` {#classexot_1_1utilities_1_1CLI_1a82aa2f99d6f51242ebe72058ddf733cf}

Prepends a section to the help message.

#### Parameters
* `title` The title 

* `content` The content

#### `public void `[`append_section`](#classexot_1_1utilities_1_1CLI_1ad2147c937d33bdd91741b758d8fb4c66)`(const std::string & title,const std::string & content)` {#classexot_1_1utilities_1_1CLI_1ad2147c937d33bdd91741b758d8fb4c66}

Appends a section to the help message.

#### Parameters
* `title` The title 

* `content` The content

#### `public void `[`add_description`](#classexot_1_1utilities_1_1CLI_1ac9b259f77371ce704f014e1f9257b5e3)`(const std::string & description)` {#classexot_1_1utilities_1_1CLI_1ac9b259f77371ce704f014e1f9257b5e3}

Adds a description section to the help message.

#### Parameters
* `description` The description

#### `public void `[`add_example`](#classexot_1_1utilities_1_1CLI_1a000017d711c418c918ede732835837d0)`(const std::string & example)` {#classexot_1_1utilities_1_1CLI_1a000017d711c418c918ede732835837d0}

Adds an example section to the help message.

#### Parameters
* `example` The example

#### `public bool `[`parse`](#classexot_1_1utilities_1_1CLI_1ad6c92dd6520b8652b02fa256d1ad721b)`(int argc,char ** argv)` {#classexot_1_1utilities_1_1CLI_1ad6c92dd6520b8652b02fa256d1ad721b}

Parses the command line arguments.

#### Parameters
* `argc` The argc from main 

* `argv` The argv from main

#### Returns
True if successful, false if parsing error occurred

#### `public template<>`  <br/>`inline void `[`collect_descriptions`](#classexot_1_1utilities_1_1CLI_1a822f6f2c505cff659f4ed760da0256a3)`(Ts &&... ts)` {#classexot_1_1utilities_1_1CLI_1a822f6f2c505cff659f4ed760da0256a3}

# class `exot::utilities::JsonConfig` {#classexot_1_1utilities_1_1JsonConfig}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public clipp::group `[`get_cli_configuration`](#classexot_1_1utilities_1_1JsonConfig_1add712c412449b61784b9e78afd7f0163)`()` | 
`public nlohmann::json `[`get`](#classexot_1_1utilities_1_1JsonConfig_1a0a41b38132652a701d1ea0f6a7303c26)`() const` | 
`public nlohmann::json::reference `[`get_ref`](#classexot_1_1utilities_1_1JsonConfig_1a18ae3018dd730cb9a1bc5d9a99906c81)`()` | 
`public nlohmann::json::const_reference `[`get_const_ref`](#classexot_1_1utilities_1_1JsonConfig_1ad10d6ecb7d9e23368ce70223727ceecb)`() const` | 
`public std::string `[`get_filename_or_data`](#classexot_1_1utilities_1_1JsonConfig_1a8b2961433fed7592f10d19e2fd53983e)`() const` | 
`public void `[`set_with_file`](#classexot_1_1utilities_1_1JsonConfig_1a5bbaa19c476aa77a1f3e2c72fa4c81f1)`(const char * file)` | 
`public void `[`set_with_file`](#classexot_1_1utilities_1_1JsonConfig_1abbcc684b810bc458075e99975a29a329)`(const std::string & file)` | 
`public void `[`set_with_file`](#classexot_1_1utilities_1_1JsonConfig_1a54180203c882da0e2ac466bf8dd4ab21)`(std::string && file)` | 
`public void `[`set_with_string`](#classexot_1_1utilities_1_1JsonConfig_1a9d13c9fc4b935d6757098bf2a6564ff3)`(const char * string)` | 
`public void `[`set_with_string`](#classexot_1_1utilities_1_1JsonConfig_1a8959d05bbde980bb7310d53fbcf320c0)`(const std::string & string)` | 
`public void `[`set_with_string`](#classexot_1_1utilities_1_1JsonConfig_1afa4801a612396badc2c4545762470448)`(std::string && string)` | 

## Members

#### `public clipp::group `[`get_cli_configuration`](#classexot_1_1utilities_1_1JsonConfig_1add712c412449b61784b9e78afd7f0163)`()` {#classexot_1_1utilities_1_1JsonConfig_1add712c412449b61784b9e78afd7f0163}

#### `public nlohmann::json `[`get`](#classexot_1_1utilities_1_1JsonConfig_1a0a41b38132652a701d1ea0f6a7303c26)`() const` {#classexot_1_1utilities_1_1JsonConfig_1a0a41b38132652a701d1ea0f6a7303c26}

#### `public nlohmann::json::reference `[`get_ref`](#classexot_1_1utilities_1_1JsonConfig_1a18ae3018dd730cb9a1bc5d9a99906c81)`()` {#classexot_1_1utilities_1_1JsonConfig_1a18ae3018dd730cb9a1bc5d9a99906c81}

#### `public nlohmann::json::const_reference `[`get_const_ref`](#classexot_1_1utilities_1_1JsonConfig_1ad10d6ecb7d9e23368ce70223727ceecb)`() const` {#classexot_1_1utilities_1_1JsonConfig_1ad10d6ecb7d9e23368ce70223727ceecb}

#### `public std::string `[`get_filename_or_data`](#classexot_1_1utilities_1_1JsonConfig_1a8b2961433fed7592f10d19e2fd53983e)`() const` {#classexot_1_1utilities_1_1JsonConfig_1a8b2961433fed7592f10d19e2fd53983e}

#### `public void `[`set_with_file`](#classexot_1_1utilities_1_1JsonConfig_1a5bbaa19c476aa77a1f3e2c72fa4c81f1)`(const char * file)` {#classexot_1_1utilities_1_1JsonConfig_1a5bbaa19c476aa77a1f3e2c72fa4c81f1}

#### `public void `[`set_with_file`](#classexot_1_1utilities_1_1JsonConfig_1abbcc684b810bc458075e99975a29a329)`(const std::string & file)` {#classexot_1_1utilities_1_1JsonConfig_1abbcc684b810bc458075e99975a29a329}

#### `public void `[`set_with_file`](#classexot_1_1utilities_1_1JsonConfig_1a54180203c882da0e2ac466bf8dd4ab21)`(std::string && file)` {#classexot_1_1utilities_1_1JsonConfig_1a54180203c882da0e2ac466bf8dd4ab21}

#### `public void `[`set_with_string`](#classexot_1_1utilities_1_1JsonConfig_1a9d13c9fc4b935d6757098bf2a6564ff3)`(const char * string)` {#classexot_1_1utilities_1_1JsonConfig_1a9d13c9fc4b935d6757098bf2a6564ff3}

#### `public void `[`set_with_string`](#classexot_1_1utilities_1_1JsonConfig_1a8959d05bbde980bb7310d53fbcf320c0)`(const std::string & string)` {#classexot_1_1utilities_1_1JsonConfig_1a8959d05bbde980bb7310d53fbcf320c0}

#### `public void `[`set_with_string`](#classexot_1_1utilities_1_1JsonConfig_1afa4801a612396badc2c4545762470448)`(std::string && string)` {#classexot_1_1utilities_1_1JsonConfig_1afa4801a612396badc2c4545762470448}

# class `exot::utilities::Logging` {#classexot_1_1utilities_1_1Logging}

Class that encapsulates all logging options and is responsible for creating loggers.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`Logging`](#classexot_1_1utilities_1_1Logging_1a9f740b59c0bc95cf5d740e114fd1c9a6)`(`[`settings`](#structexot_1_1utilities_1_1Logging_1_1settings)` & conf)` | 
`typedef `[`logger_pointer`](#classexot_1_1utilities_1_1Logging_1a60f1d5738aa16e2462dddd886646af36) | 

## Members

#### `public  `[`Logging`](#classexot_1_1utilities_1_1Logging_1a9f740b59c0bc95cf5d740e114fd1c9a6)`(`[`settings`](#structexot_1_1utilities_1_1Logging_1_1settings)` & conf)` {#classexot_1_1utilities_1_1Logging_1a9f740b59c0bc95cf5d740e114fd1c9a6}

#### `typedef `[`logger_pointer`](#classexot_1_1utilities_1_1Logging_1a60f1d5738aa16e2462dddd886646af36) {#classexot_1_1utilities_1_1Logging_1a60f1d5738aa16e2462dddd886646af36}

# class `exot::utilities::TimeKeeper` {#classexot_1_1utilities_1_1TimeKeeper}

Class used for keeping track of sleep time and offsets.

The time keeper provides an interface for sleeping with offset and overhead accounting, can use different clock sources and sleep functions, and can report interval, offset, and differential statistics of sleep durations.

#### Parameters
* `Clock` A clock type, which provides a `now()` method, e.g. `std::chrono::steady_clock`

* `EnableLogging` A boolean value to indicate use internal offset logging 

* `RepGranularity` Chrono duration granularity used for time reporting 

* `Granularity` Chrono duration granularity used for time keeping, e.g. `std::chrono::nanoseconds`

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  explicit `[`TimeKeeper`](#classexot_1_1utilities_1_1TimeKeeper_1aeb1a3e5c0b491b71fbab14f7c771eded)`(std::shared_ptr< spdlog::logger > logger,sleep_func_type sleep_function,typename chrono_granularity::rep minimum_percentage,unsigned int log_size_to_reserve,unsigned int overhead_iterations) = default` | Constructs the object with all options.
`public inline void `[`begin`](#classexot_1_1utilities_1_1TimeKeeper_1af604746a8f640869591c7938807b4f65)`()` | Initialises the time keeping reference time.
`public inline auto `[`now`](#classexot_1_1utilities_1_1TimeKeeper_1aa797241847aa0ad2d7510c99c37d168c)`() const` | 
`public inline auto `[`update_offset`](#classexot_1_1utilities_1_1TimeKeeper_1a65487b5b3172d7bc7b6232af223b0e8d)`()` | Updates the offset used to compensate for the mismatch between the desired and the actual time point.
`public inline void `[`sleep`](#classexot_1_1utilities_1_1TimeKeeper_1ae4bded93b22dd0e8a34b15f1e7a397ad)`(chrono_granularity duration)` | Sleeps for the specified duration, taking account of the current offset.
`public template<>`  <br/>`inline void `[`run_every`](#classexot_1_1utilities_1_1TimeKeeper_1a995daecebb86a90beb19134a50832eb2)`(chrono_granularity period,std::function< bool(void)> && predicate,Callable && callable,Args &&... args)` | Invokes a callable object repeatedly with a constant period, until some predicate is satisfied.
`public inline std::vector< std::array< reporting_granularity, 3 > > `[`dump_log`](#classexot_1_1utilities_1_1TimeKeeper_1a6cbe6407bb685dc89ad7317d4a9f4da9)`()` | Dumps the logged actual, desired, and offset durations.
`public inline auto `[`offset_statistics`](#classexot_1_1utilities_1_1TimeKeeper_1ae15e58e3a67970754cdc81ccd64dd969)`()` | Calculates the mean and standard deviation of calculated offsets.
`public inline auto `[`differential_statistics`](#classexot_1_1utilities_1_1TimeKeeper_1aeb4b7c40a0e9737d2cdec6ba6610287b)`()` | Calculates the mean and deviation of differences between actual and desired sleep durations, essentially an alias of `[offset_statistics()](#classexot_1_1utilities_1_1TimeKeeper_1ae15e58e3a67970754cdc81ccd64dd969)`.
`public inline auto `[`interval_statistics`](#classexot_1_1utilities_1_1TimeKeeper_1a032297f54ce957ef9aa128aca2c8111d)`()` | Calculates the mean and standard deviation of the intervals between the consecutive actual time points.
`typedef `[`clock_type`](#classexot_1_1utilities_1_1TimeKeeper_1acc2febf9b47a96bfc81fec9baaa16c2d) | 
`typedef `[`chrono_granularity`](#classexot_1_1utilities_1_1TimeKeeper_1a63e183d85b88cbe3fdae6fdf8cafdfb3) | 
`typedef `[`reporting_granularity`](#classexot_1_1utilities_1_1TimeKeeper_1a1e5ff6394387868f0f7072d965fa3352) | 
`typedef `[`sleep_func_type`](#classexot_1_1utilities_1_1TimeKeeper_1ab92d65ebbc2d7efbd497f11b20400120) | 
`typedef `[`sleep_func_rep`](#classexot_1_1utilities_1_1TimeKeeper_1a49f602c620a918344e4041b715431d33) | 
`typedef `[`sleep_func_period`](#classexot_1_1utilities_1_1TimeKeeper_1abe25e7d2e2aabd92c2ad05cd9f2cd9a5) | 

## Members

#### `public inline  explicit `[`TimeKeeper`](#classexot_1_1utilities_1_1TimeKeeper_1aeb1a3e5c0b491b71fbab14f7c771eded)`(std::shared_ptr< spdlog::logger > logger,sleep_func_type sleep_function,typename chrono_granularity::rep minimum_percentage,unsigned int log_size_to_reserve,unsigned int overhead_iterations) = default` {#classexot_1_1utilities_1_1TimeKeeper_1aeb1a3e5c0b491b71fbab14f7c771eded}

Constructs the object with all options.

In order to allow the use of different sleep functions (e.g. `nanosleep`, `std::this_thread::sleep_for`, `boost::this_fiber::sleep_for`, etc.) the constructor takes a pointer to that function, instead of using the older template parameter.

#### Parameters
* `logger` A shared pointer to application logger 

* `sleep_function` The address of a sleep function, by default uses the `std::this_thread::sleep_for` function. 

* `minimum_percentage` The minimum percentage of the passed sleep duration that will be passed to the sleeping function. The value is used in the call to `std::max`, which result is passed to the actual sleeping function. 

* `log_size_to_reserve` The reserved vector size for logging desired, actual, and offset durations 

* `overhead_iterations` The number of iterations used for calculating the offset of a sequence of calls to `clock_type::now()` and the necessary subtraction used to obtain the duration between the calls.

#### `public inline void `[`begin`](#classexot_1_1utilities_1_1TimeKeeper_1af604746a8f640869591c7938807b4f65)`()` {#classexot_1_1utilities_1_1TimeKeeper_1af604746a8f640869591c7938807b4f65}

Initialises the time keeping reference time.

There is no need to keep a `start_` variable, because `desired_` is incremented with every call to the `[sleep()](#classexot_1_1utilities_1_1TimeKeeper_1ae4bded93b22dd0e8a34b15f1e7a397ad)` method.

#### `public inline auto `[`now`](#classexot_1_1utilities_1_1TimeKeeper_1aa797241847aa0ad2d7510c99c37d168c)`() const` {#classexot_1_1utilities_1_1TimeKeeper_1aa797241847aa0ad2d7510c99c37d168c}

#### `public inline auto `[`update_offset`](#classexot_1_1utilities_1_1TimeKeeper_1a65487b5b3172d7bc7b6232af223b0e8d)`()` {#classexot_1_1utilities_1_1TimeKeeper_1a65487b5b3172d7bc7b6232af223b0e8d}

Updates the offset used to compensate for the mismatch between the desired and the actual time point.

#### `public inline void `[`sleep`](#classexot_1_1utilities_1_1TimeKeeper_1ae4bded93b22dd0e8a34b15f1e7a397ad)`(chrono_granularity duration)` {#classexot_1_1utilities_1_1TimeKeeper_1ae4bded93b22dd0e8a34b15f1e7a397ad}

Sleeps for the specified duration, taking account of the current offset.

Uses the sleep function provided in the time keeper constructor.

#### Parameters
* `duration` The desired sleep duration

#### `public template<>`  <br/>`inline void `[`run_every`](#classexot_1_1utilities_1_1TimeKeeper_1a995daecebb86a90beb19134a50832eb2)`(chrono_granularity period,std::function< bool(void)> && predicate,Callable && callable,Args &&... args)` {#classexot_1_1utilities_1_1TimeKeeper_1a995daecebb86a90beb19134a50832eb2}

Invokes a callable object repeatedly with a constant period, until some predicate is satisfied.

#### Parameters
* `period` The period at which the function is called 

* `predicate` A function returning true if continuing, false otherwise 

* `callable` A callable object 

* `args` Arguments to the callable object, optional (`sizeof...(args)` can be zero)

#### Parameters
* `Callable` A callable type 

* `Args` Argument types to the callable object

#### `public inline std::vector< std::array< reporting_granularity, 3 > > `[`dump_log`](#classexot_1_1utilities_1_1TimeKeeper_1a6cbe6407bb685dc89ad7317d4a9f4da9)`()` {#classexot_1_1utilities_1_1TimeKeeper_1a6cbe6407bb685dc89ad7317d4a9f4da9}

Dumps the logged actual, desired, and offset durations.

#### Returns
A vector of the durations arranged in a fixed-size array.

#### `public inline auto `[`offset_statistics`](#classexot_1_1utilities_1_1TimeKeeper_1ae15e58e3a67970754cdc81ccd64dd969)`()` {#classexot_1_1utilities_1_1TimeKeeper_1ae15e58e3a67970754cdc81ccd64dd969}

Calculates the mean and standard deviation of calculated offsets.

#### Returns
A string with formatted values using the chosen reporting granularity.

#### `public inline auto `[`differential_statistics`](#classexot_1_1utilities_1_1TimeKeeper_1aeb4b7c40a0e9737d2cdec6ba6610287b)`()` {#classexot_1_1utilities_1_1TimeKeeper_1aeb4b7c40a0e9737d2cdec6ba6610287b}

Calculates the mean and deviation of differences between actual and desired sleep durations, essentially an alias of `[offset_statistics()](#classexot_1_1utilities_1_1TimeKeeper_1ae15e58e3a67970754cdc81ccd64dd969)`.

#### Returns
A string with formatted values using the chosen reporting granularity.

#### `public inline auto `[`interval_statistics`](#classexot_1_1utilities_1_1TimeKeeper_1a032297f54ce957ef9aa128aca2c8111d)`()` {#classexot_1_1utilities_1_1TimeKeeper_1a032297f54ce957ef9aa128aca2c8111d}

Calculates the mean and standard deviation of the intervals between the consecutive actual time points.

#### Returns
A string with formatted values using the chosen reporting granularity.

#### `typedef `[`clock_type`](#classexot_1_1utilities_1_1TimeKeeper_1acc2febf9b47a96bfc81fec9baaa16c2d) {#classexot_1_1utilities_1_1TimeKeeper_1acc2febf9b47a96bfc81fec9baaa16c2d}

#### `typedef `[`chrono_granularity`](#classexot_1_1utilities_1_1TimeKeeper_1a63e183d85b88cbe3fdae6fdf8cafdfb3) {#classexot_1_1utilities_1_1TimeKeeper_1a63e183d85b88cbe3fdae6fdf8cafdfb3}

#### `typedef `[`reporting_granularity`](#classexot_1_1utilities_1_1TimeKeeper_1a1e5ff6394387868f0f7072d965fa3352) {#classexot_1_1utilities_1_1TimeKeeper_1a1e5ff6394387868f0f7072d965fa3352}

#### `typedef `[`sleep_func_type`](#classexot_1_1utilities_1_1TimeKeeper_1ab92d65ebbc2d7efbd497f11b20400120) {#classexot_1_1utilities_1_1TimeKeeper_1ab92d65ebbc2d7efbd497f11b20400120}

#### `typedef `[`sleep_func_rep`](#classexot_1_1utilities_1_1TimeKeeper_1a49f602c620a918344e4041b715431d33) {#classexot_1_1utilities_1_1TimeKeeper_1a49f602c620a918344e4041b715431d33}

#### `typedef `[`sleep_func_period`](#classexot_1_1utilities_1_1TimeKeeper_1abe25e7d2e2aabd92c2ad05cd9f2cd9a5) {#classexot_1_1utilities_1_1TimeKeeper_1abe25e7d2e2aabd92c2ad05cd9f2cd9a5}

# struct `exot::utilities::aligned_t` {#structexot_1_1utilities_1_1aligned__t}

Aligned type wrapper.

#### Parameters
* `T` The value type to wrap 

* `A` The desired alignment 

* `<unnamed>` Template helper (only fundamental types allowed)

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public T `[`_value`](#structexot_1_1utilities_1_1aligned__t_1afb2fc262241f278d2a77d0fcd347b958) | 
`public  `[`aligned_t`](#structexot_1_1utilities_1_1aligned__t_1afc43d397cfdabc2b22395e204dd7739f)`() = default` | Default constructor
`public inline  `[`aligned_t`](#structexot_1_1utilities_1_1aligned__t_1a6df38ffabc0af9d48b1688691182d3d8)`(value_type && value)` | Copy constructor for value types.
`public inline  `[`operator T`](#structexot_1_1utilities_1_1aligned__t_1a992bb2fe171a74898cb6483d61fcfded)`()` | Proxy to the value.
`public inline T * `[`operator&`](#structexot_1_1utilities_1_1aligned__t_1ab0c9375180d2ec8bdba3b22830208fa1)`()` | Proxy to the pointer to the value.
`typedef `[`value_type`](#structexot_1_1utilities_1_1aligned__t_1a15b2d455a45ab394d92df7adf4ed7389) | 
`typedef `[`this_type`](#structexot_1_1utilities_1_1aligned__t_1a0e3cab223ab8a4bde55ed29b3bc5f6f3) | 

## Members

#### `public T `[`_value`](#structexot_1_1utilities_1_1aligned__t_1afb2fc262241f278d2a77d0fcd347b958) {#structexot_1_1utilities_1_1aligned__t_1afb2fc262241f278d2a77d0fcd347b958}

#### `public  `[`aligned_t`](#structexot_1_1utilities_1_1aligned__t_1afc43d397cfdabc2b22395e204dd7739f)`() = default` {#structexot_1_1utilities_1_1aligned__t_1afc43d397cfdabc2b22395e204dd7739f}

Default constructor

#### `public inline  `[`aligned_t`](#structexot_1_1utilities_1_1aligned__t_1a6df38ffabc0af9d48b1688691182d3d8)`(value_type && value)` {#structexot_1_1utilities_1_1aligned__t_1a6df38ffabc0af9d48b1688691182d3d8}

Copy constructor for value types.

#### Parameters
* `value` The value

#### `public inline  `[`operator T`](#structexot_1_1utilities_1_1aligned__t_1a992bb2fe171a74898cb6483d61fcfded)`()` {#structexot_1_1utilities_1_1aligned__t_1a992bb2fe171a74898cb6483d61fcfded}

Proxy to the value.

#### `public inline T * `[`operator&`](#structexot_1_1utilities_1_1aligned__t_1ab0c9375180d2ec8bdba3b22830208fa1)`()` {#structexot_1_1utilities_1_1aligned__t_1ab0c9375180d2ec8bdba3b22830208fa1}

Proxy to the pointer to the value.

#### `typedef `[`value_type`](#structexot_1_1utilities_1_1aligned__t_1a15b2d455a45ab394d92df7adf4ed7389) {#structexot_1_1utilities_1_1aligned__t_1a15b2d455a45ab394d92df7adf4ed7389}

#### `typedef `[`this_type`](#structexot_1_1utilities_1_1aligned__t_1a0e3cab223ab8a4bde55ed29b3bc5f6f3) {#structexot_1_1utilities_1_1aligned__t_1a0e3cab223ab8a4bde55ed29b3bc5f6f3}

# struct `exot::utilities::AlignedAllocator` {#structexot_1_1utilities_1_1AlignedAllocator}

Aligned allocator to use with STL containers.

#### Parameters
* `T` The value type 

* `Al` The desired alignment

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a01d8c4fd67dbfb0345f9bde931520511)`() = default` | 
`public  `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a75f27b9fb8760ad44c58bb442d1473d8)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)` & other) = default` | 
`public `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)` & `[`operator=`](#structexot_1_1utilities_1_1AlignedAllocator_1a83ca3e4ce078d5f4c49a745f8a3d1f4f)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)` & other) = delete` | 
`public template<>`  <br/>`inline  `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a42c5d9968ccdfbeffe323fba46be9abb)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< U, Al > &) noexcept` | 
`public  `[`~AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a26c0db935df972a1b65f8cd2e2c8dbaf)`() = default` | 
`public inline T * `[`allocate`](#structexot_1_1utilities_1_1AlignedAllocator_1afa710923639c5c0da4a70db56a501e15)`(std::size_t n) const` | Allocates memory.
`public inline void `[`deallocate`](#structexot_1_1utilities_1_1AlignedAllocator_1a465d33c7f3c4c1a87288cb119a0d5a5b)`(T * p,std::size_t n) const` | Frees memory.
`typedef `[`value_type`](#structexot_1_1utilities_1_1AlignedAllocator_1af19b5190eca4ea5fff7e4ef870c2e918) | 
`typedef `[`size_type`](#structexot_1_1utilities_1_1AlignedAllocator_1aa149819dfbf8287ad362ba2fd5dba1dc) | 
`typedef `[`difference_type`](#structexot_1_1utilities_1_1AlignedAllocator_1a2645b5aeeb975b13bc6f472451089d20) | 
`typedef `[`propagate_on_container_move_assignment`](#structexot_1_1utilities_1_1AlignedAllocator_1a05042fa5eb0461c9b556aebcfafa678b) | 
`typedef `[`is_always_equal`](#structexot_1_1utilities_1_1AlignedAllocator_1a8f139f9713d924991a752090626f7dfc) | 

## Members

#### `public  `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a01d8c4fd67dbfb0345f9bde931520511)`() = default` {#structexot_1_1utilities_1_1AlignedAllocator_1a01d8c4fd67dbfb0345f9bde931520511}

#### `public  `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a75f27b9fb8760ad44c58bb442d1473d8)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)` & other) = default` {#structexot_1_1utilities_1_1AlignedAllocator_1a75f27b9fb8760ad44c58bb442d1473d8}

#### `public `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)` & `[`operator=`](#structexot_1_1utilities_1_1AlignedAllocator_1a83ca3e4ce078d5f4c49a745f8a3d1f4f)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)` & other) = delete` {#structexot_1_1utilities_1_1AlignedAllocator_1a83ca3e4ce078d5f4c49a745f8a3d1f4f}

#### `public template<>`  <br/>`inline  `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a42c5d9968ccdfbeffe323fba46be9abb)`(const `[`AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator)`< U, Al > &) noexcept` {#structexot_1_1utilities_1_1AlignedAllocator_1a42c5d9968ccdfbeffe323fba46be9abb}

#### `public  `[`~AlignedAllocator`](#structexot_1_1utilities_1_1AlignedAllocator_1a26c0db935df972a1b65f8cd2e2c8dbaf)`() = default` {#structexot_1_1utilities_1_1AlignedAllocator_1a26c0db935df972a1b65f8cd2e2c8dbaf}

#### `public inline T * `[`allocate`](#structexot_1_1utilities_1_1AlignedAllocator_1afa710923639c5c0da4a70db56a501e15)`(std::size_t n) const` {#structexot_1_1utilities_1_1AlignedAllocator_1afa710923639c5c0da4a70db56a501e15}

Allocates memory.

Uses the `posix_memalign` function from cstdlib.

#### Parameters
* `n` The size to allocate

#### `public inline void `[`deallocate`](#structexot_1_1utilities_1_1AlignedAllocator_1a465d33c7f3c4c1a87288cb119a0d5a5b)`(T * p,std::size_t n) const` {#structexot_1_1utilities_1_1AlignedAllocator_1a465d33c7f3c4c1a87288cb119a0d5a5b}

Frees memory.

#### Parameters
* `p` The pointer to memory to deallocate 

* `n` The count to deallocate (unused)

#### `typedef `[`value_type`](#structexot_1_1utilities_1_1AlignedAllocator_1af19b5190eca4ea5fff7e4ef870c2e918) {#structexot_1_1utilities_1_1AlignedAllocator_1af19b5190eca4ea5fff7e4ef870c2e918}

#### `typedef `[`size_type`](#structexot_1_1utilities_1_1AlignedAllocator_1aa149819dfbf8287ad362ba2fd5dba1dc) {#structexot_1_1utilities_1_1AlignedAllocator_1aa149819dfbf8287ad362ba2fd5dba1dc}

#### `typedef `[`difference_type`](#structexot_1_1utilities_1_1AlignedAllocator_1a2645b5aeeb975b13bc6f472451089d20) {#structexot_1_1utilities_1_1AlignedAllocator_1a2645b5aeeb975b13bc6f472451089d20}

#### `typedef `[`propagate_on_container_move_assignment`](#structexot_1_1utilities_1_1AlignedAllocator_1a05042fa5eb0461c9b556aebcfafa678b) {#structexot_1_1utilities_1_1AlignedAllocator_1a05042fa5eb0461c9b556aebcfafa678b}

#### `typedef `[`is_always_equal`](#structexot_1_1utilities_1_1AlignedAllocator_1a8f139f9713d924991a752090626f7dfc) {#structexot_1_1utilities_1_1AlignedAllocator_1a8f139f9713d924991a752090626f7dfc}

# struct `exot::utilities::bad_alloc` {#structexot_1_1utilities_1_1bad__alloc}

```
struct exot::utilities::bad_alloc
  : public exception
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  `[`bad_alloc`](#structexot_1_1utilities_1_1bad__alloc_1abf4e129c17a99adae7a61f8213e97f98)`(std::string err)` | 
`public inline  `[`bad_alloc`](#structexot_1_1utilities_1_1bad__alloc_1a8cc9118fd12bdcd1e164a2ed92e5d997)`(const char * err)` | 
`public inline  `[`bad_alloc`](#structexot_1_1utilities_1_1bad__alloc_1a2c2a9b5163a0fe0a6b0a91f473db6327)`()` | 
`public inline const char * `[`what`](#structexot_1_1utilities_1_1bad__alloc_1a8f0a6820721338e1d9f792a2bd245fd8)`() const` | 

## Members

#### `public inline  `[`bad_alloc`](#structexot_1_1utilities_1_1bad__alloc_1abf4e129c17a99adae7a61f8213e97f98)`(std::string err)` {#structexot_1_1utilities_1_1bad__alloc_1abf4e129c17a99adae7a61f8213e97f98}

#### `public inline  `[`bad_alloc`](#structexot_1_1utilities_1_1bad__alloc_1a8cc9118fd12bdcd1e164a2ed92e5d997)`(const char * err)` {#structexot_1_1utilities_1_1bad__alloc_1a8cc9118fd12bdcd1e164a2ed92e5d997}

#### `public inline  `[`bad_alloc`](#structexot_1_1utilities_1_1bad__alloc_1a2c2a9b5163a0fe0a6b0a91f473db6327)`()` {#structexot_1_1utilities_1_1bad__alloc_1a2c2a9b5163a0fe0a6b0a91f473db6327}

#### `public inline const char * `[`what`](#structexot_1_1utilities_1_1bad__alloc_1a8f0a6820721338e1d9f792a2bd245fd8)`() const` {#structexot_1_1utilities_1_1bad__alloc_1a8f0a6820721338e1d9f792a2bd245fd8}

# struct `exot::utilities::configurable` {#structexot_1_1utilities_1_1configurable}

```
struct exot::utilities::configurable
  : public exot::utilities::configurable_base
```  

Mixin for use in CRTP patterns to introduce configurability to compatible classes.

To take advantage of the configurable mixin the class of type D should have a function returning a string: name(). These are used to subset configuration structures using JSON pointers. 
> Todo: Provide a way for this to return a clipp::group for [CLI](#classexot_1_1utilities_1_1CLI) config

#### Parameters
* `D` The type to be mixed-in.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline const char * `[`name`](#structexot_1_1utilities_1_1configurable_1ada61760b91278110ecf17e239676c4b1)`() const` | 
`public inline void `[`set_json`](#structexot_1_1utilities_1_1configurable_1ad85a6c6a1addb6610417188a85a9a64b)`(const nlohmann::json & root)` | Sets the internal JSON config.
`public inline nlohmann::json `[`get_json`](#structexot_1_1utilities_1_1configurable_1a9958df5c8dc7f0d6170095d4a8283b2c)`() const` | Gets the internal JSON config's value.
`public inline const nlohmann::json & `[`get_json_const_ref`](#structexot_1_1utilities_1_1configurable_1af18f281caf024befad08d8f437f5030a)`() const` | Gets the internal JSON config as a constant reference.
`public void `[`configure`](#structexot_1_1utilities_1_1configurable_1a80a590d62a1ea06a93742917e44e51d8)`()` | Configure, to be implemented in the derived class.
`public inline std::string `[`describe`](#structexot_1_1utilities_1_1configurable_1a93d737a516584dcea6c7a77a6dfea7f1)`()` | 
`protected inline constexpr D & `[`derived`](#structexot_1_1utilities_1_1configurable_1ad3b62831da95de38e01d6a934b35709a)`()` | CRTP helper for casting this class to the CRTP-derived class.
`protected inline constexpr const D & `[`derived`](#structexot_1_1utilities_1_1configurable_1a9bdca8d480d080b1bba8e7a547a0785a)`() const` | CRTP helper for casting this class to the CRTP-derived class.
`protected inline nlohmann::json::json_pointer `[`get_json_pointer`](#structexot_1_1utilities_1_1configurable_1aa3b92d2cadc5a2ad2a306482be3b41be)`() const` | Gets a JSON pointer to the class-specific configuration.
`protected inline nlohmann::json & `[`get_json_ref`](#structexot_1_1utilities_1_1configurable_1a7ea596bc65c334fd83522a86f489e0e1)`()` | Gets a reference to the contained JSON config.
`protected template<>`  <br/>`inline bool `[`bind_and_describe_data`](#structexot_1_1utilities_1_1configurable_1a13cfa76fe284dc58d691db8b20ebbfc0)`(const char * key,T & to,std::string && description)` | Bind a JSON value at a key to a local variable.

## Members

#### `public inline const char * `[`name`](#structexot_1_1utilities_1_1configurable_1ada61760b91278110ecf17e239676c4b1)`() const` {#structexot_1_1utilities_1_1configurable_1ada61760b91278110ecf17e239676c4b1}

#### `public inline void `[`set_json`](#structexot_1_1utilities_1_1configurable_1ad85a6c6a1addb6610417188a85a9a64b)`(const nlohmann::json & root)` {#structexot_1_1utilities_1_1configurable_1ad85a6c6a1addb6610417188a85a9a64b}

Sets the internal JSON config.

#### Parameters
* `root` The root JSON file/config

#### `public inline nlohmann::json `[`get_json`](#structexot_1_1utilities_1_1configurable_1a9958df5c8dc7f0d6170095d4a8283b2c)`() const` {#structexot_1_1utilities_1_1configurable_1a9958df5c8dc7f0d6170095d4a8283b2c}

Gets the internal JSON config's value.

#### Returns
The value of the JSON

#### `public inline const nlohmann::json & `[`get_json_const_ref`](#structexot_1_1utilities_1_1configurable_1af18f281caf024befad08d8f437f5030a)`() const` {#structexot_1_1utilities_1_1configurable_1af18f281caf024befad08d8f437f5030a}

Gets the internal JSON config as a constant reference.

#### Returns
The constant reference to the JSON.

#### `public void `[`configure`](#structexot_1_1utilities_1_1configurable_1a80a590d62a1ea06a93742917e44e51d8)`()` {#structexot_1_1utilities_1_1configurable_1a80a590d62a1ea06a93742917e44e51d8}

Configure, to be implemented in the derived class.

#### `public inline std::string `[`describe`](#structexot_1_1utilities_1_1configurable_1a93d737a516584dcea6c7a77a6dfea7f1)`()` {#structexot_1_1utilities_1_1configurable_1a93d737a516584dcea6c7a77a6dfea7f1}

#### `protected inline constexpr D & `[`derived`](#structexot_1_1utilities_1_1configurable_1ad3b62831da95de38e01d6a934b35709a)`()` {#structexot_1_1utilities_1_1configurable_1ad3b62831da95de38e01d6a934b35709a}

CRTP helper for casting this class to the CRTP-derived class.

#### Returns
The reference to this using the pointer to the base class

#### `protected inline constexpr const D & `[`derived`](#structexot_1_1utilities_1_1configurable_1a9bdca8d480d080b1bba8e7a547a0785a)`() const` {#structexot_1_1utilities_1_1configurable_1a9bdca8d480d080b1bba8e7a547a0785a}

CRTP helper for casting this class to the CRTP-derived class.

#### Returns
The const reference to this casted to the base class

#### `protected inline nlohmann::json::json_pointer `[`get_json_pointer`](#structexot_1_1utilities_1_1configurable_1aa3b92d2cadc5a2ad2a306482be3b41be)`() const` {#structexot_1_1utilities_1_1configurable_1aa3b92d2cadc5a2ad2a306482be3b41be}

Gets a JSON pointer to the class-specific configuration.

#### Returns
The JSON pointer to configuration.

#### `protected inline nlohmann::json & `[`get_json_ref`](#structexot_1_1utilities_1_1configurable_1a7ea596bc65c334fd83522a86f489e0e1)`()` {#structexot_1_1utilities_1_1configurable_1a7ea596bc65c334fd83522a86f489e0e1}

Gets a reference to the contained JSON config.

#### Returns
The reference to the JSON config.

#### `protected template<>`  <br/>`inline bool `[`bind_and_describe_data`](#structexot_1_1utilities_1_1configurable_1a13cfa76fe284dc58d691db8b20ebbfc0)`(const char * key,T & to,std::string && description)` {#structexot_1_1utilities_1_1configurable_1a13cfa76fe284dc58d691db8b20ebbfc0}

Bind a JSON value at a key to a local variable.

The function was refactored to allow incomplete configs to be used, in which case the JSON config was not assigned and the reference is a nullptr.

#### Parameters
* `key` The JSON key 

* `to` The reference to the local variable

#### Parameters
* `T` The type of the local variable

#### Returns
True if able to bind, false otherwise.

# struct `exot::utilities::configurable_base` {#structexot_1_1utilities_1_1configurable__base}

Base class for configurable types.

Empty base class does not increase the object size. The structure is used mostly for type checks.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_writable_to_stream< T, std::ostream, std::void_t< decltype(std::declval< std::ostream & >()<< std::declval< T & >())> >` {#structexot_1_1utilities_1_1is__writable__to__stream_3_01T_00_01std_1_1ostream_00_01std_1_1void__5d1df126fd77cfd63df8a5108f424957}

```
struct exot::utilities::is_writable_to_stream< T, std::ostream, std::void_t< decltype(std::declval< std::ostream & >()<< std::declval< T & >())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::enum_operations_enabled` {#structexot_1_1utilities_1_1enum__operations__enabled}

```
struct exot::utilities::enum_operations_enabled
  : public false_type
```  

Type trait to enable bit-wise operations for an Enum.

#### Parameters
* `Enum` The enum 

* `<unnamed>` Template helper (is enum?)

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::enum_operations_enabled< Advice >` {#structexot_1_1utilities_1_1enum__operations__enabled_3_01Advice_01_4}

```
struct exot::utilities::enum_operations_enabled< Advice >
  : public true_type
```  

Overload of [enum_operations_enabled](#structexot_1_1utilities_1_1enum__operations__enabled) for Advice.

Enables bitwise operators on the Advice enum.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::Evicter` {#structexot_1_1utilities_1_1Evicter}

Accesses memory with specific patterns.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  explicit `[`Evicter`](#structexot_1_1utilities_1_1Evicter_1abef412bf7ee230def84cde4a34d10d46)`(std::size_t addresses_per_loop,std::size_t accesses_per_loop,std::size_t overlap_parameter)` | Constructs the evicter.
`public inline  explicit `[`Evicter`](#structexot_1_1utilities_1_1Evicter_1ad60baa56fcf06dd3201e0e2272012548)`(std::size_t addresses_per_loop,std::size_t accesses_per_loop)` | Constructs the evicter.
`public inline  `[`Evicter`](#structexot_1_1utilities_1_1Evicter_1ababa8012fb514855b940820630743886)`()` | Default constructor.
`public template<>`  <br/>`inline void `[`read`](#structexot_1_1utilities_1_1Evicter_1a11ad3c855fbdafe386ccce7edb28d09d)`(T & buffer)` | Accesses (reads) addresses using a buffer.
`public template<>`  <br/>`inline void `[`read_ptrs`](#structexot_1_1utilities_1_1Evicter_1a14116196132ad0897596564d9fb96924)`(T & buffer)` | Accesses (reads) addresses contained in a buffer.
`public template<>`  <br/>`inline void `[`read`](#structexot_1_1utilities_1_1Evicter_1a8b56bafceef27463fe96c113d85e550d)`(T address,std::size_t length)` | Accesses (reads) addresses using a base pointer and length.
`public template<>`  <br/>`inline void `[`write`](#structexot_1_1utilities_1_1Evicter_1afbfea17f644443451d08511b363801d5)`(T & buffer,volatile typename T::value_type value)` | Accesses (writes) addresses using a buffer.
`public template<>`  <br/>`inline void `[`write_ptrs`](#structexot_1_1utilities_1_1Evicter_1ae83c3bd2bba4db76efd65e07c11ea3b9)`(T & buffer,volatile typename T::value_type value)` | Accesses (writes) addresses contained in a buffer.
`public template<>`  <br/>`inline void `[`write`](#structexot_1_1utilities_1_1Evicter_1a5d660a20b6cc3f779680256329ca1d12)`(T address,std::size_t length,volatile T value)` | Accesses (writes) addresses using a base pointer and length.
`public template<>`  <br/>`inline void `[`read_in_reverse`](#structexot_1_1utilities_1_1Evicter_1ab0f5851536f8274aa3e3b9205090c7c9)`(T & buffer)` | Accesses (reads) addresses using a buffer in reverse order.
`public template<>`  <br/>`inline void `[`read_ptrs_in_reverse`](#structexot_1_1utilities_1_1Evicter_1ac2d844cb429e05ec435894dd5eeb4966)`(T & buffer)` | Accesses (reads) addresses contained in a buffer in reverse order.
`public template<>`  <br/>`inline void `[`read_in_reverse`](#structexot_1_1utilities_1_1Evicter_1ab9727b00f423d4173617c7a0543f2607)`(T address,std::size_t length)` | Accesses (reads) addresses using a base pointer and length in reverse order.
`public template<>`  <br/>`inline void `[`write_in_reverse`](#structexot_1_1utilities_1_1Evicter_1a329576d581ac7886ed919f7dbfdd82ed)`(T & buffer,volatile typename T::value_type value)` | Accesses (writes) addresses using a buffer in reverse order.
`public template<>`  <br/>`inline void `[`write_ptrs_in_reverse`](#structexot_1_1utilities_1_1Evicter_1a1cbc4f7a3be22e6d24f71452b6167b49)`(T & buffer,volatile typename T::value_type value)` | Accesses (writes) addresses contained in a buffer in reverse order.
`public template<>`  <br/>`inline void `[`write_in_reverse`](#structexot_1_1utilities_1_1Evicter_1a7a98266803451cae6a8f126b2170d24a)`(T address,std::size_t length,volatile T value)` | Accesses (writes) addresses using a base pointer and length in reverse order.

## Members

#### `public inline  explicit `[`Evicter`](#structexot_1_1utilities_1_1Evicter_1abef412bf7ee230def84cde4a34d10d46)`(std::size_t addresses_per_loop,std::size_t accesses_per_loop,std::size_t overlap_parameter)` {#structexot_1_1utilities_1_1Evicter_1abef412bf7ee230def84cde4a34d10d46}

Constructs the evicter.

#### Parameters
* `addresses_per_loop` The number of addresses per loop 

* `accesses_per_loop` The number of accesses to the same address per loop 

* `overlap_parameter` The overlap parameter (step size)

#### `public inline  explicit `[`Evicter`](#structexot_1_1utilities_1_1Evicter_1ad60baa56fcf06dd3201e0e2272012548)`(std::size_t addresses_per_loop,std::size_t accesses_per_loop)` {#structexot_1_1utilities_1_1Evicter_1ad60baa56fcf06dd3201e0e2272012548}

Constructs the evicter.

#### Parameters
* `addresses_per_loop` The number of addresses per loop 

* `accesses_per_loop` The number of accesses to the same address per loop

#### `public inline  `[`Evicter`](#structexot_1_1utilities_1_1Evicter_1ababa8012fb514855b940820630743886)`()` {#structexot_1_1utilities_1_1Evicter_1ababa8012fb514855b940820630743886}

Default constructor.

#### `public template<>`  <br/>`inline void `[`read`](#structexot_1_1utilities_1_1Evicter_1a11ad3c855fbdafe386ccce7edb28d09d)`(T & buffer)` {#structexot_1_1utilities_1_1Evicter_1a11ad3c855fbdafe386ccce7edb28d09d}

Accesses (reads) addresses using a buffer.

#### Parameters
* `buffer` The buffer

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with non-pointer value type)

#### `public template<>`  <br/>`inline void `[`read_ptrs`](#structexot_1_1utilities_1_1Evicter_1a14116196132ad0897596564d9fb96924)`(T & buffer)` {#structexot_1_1utilities_1_1Evicter_1a14116196132ad0897596564d9fb96924}

Accesses (reads) addresses contained in a buffer.

#### Parameters
* `buffer` The buffer

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with pointer value type)

#### `public template<>`  <br/>`inline void `[`read`](#structexot_1_1utilities_1_1Evicter_1a8b56bafceef27463fe96c113d85e550d)`(T address,std::size_t length)` {#structexot_1_1utilities_1_1Evicter_1a8b56bafceef27463fe96c113d85e550d}

Accesses (reads) addresses using a base pointer and length.

#### Parameters
* `address` The address 

* `length` The length

#### Parameters
* `T` The type 

* `<unnamed>` Template helper (only pointer types)

#### `public template<>`  <br/>`inline void `[`write`](#structexot_1_1utilities_1_1Evicter_1afbfea17f644443451d08511b363801d5)`(T & buffer,volatile typename T::value_type value)` {#structexot_1_1utilities_1_1Evicter_1afbfea17f644443451d08511b363801d5}

Accesses (writes) addresses using a buffer.

#### Parameters
* `buffer` The buffer

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with non-pointer value type)

#### `public template<>`  <br/>`inline void `[`write_ptrs`](#structexot_1_1utilities_1_1Evicter_1ae83c3bd2bba4db76efd65e07c11ea3b9)`(T & buffer,volatile typename T::value_type value)` {#structexot_1_1utilities_1_1Evicter_1ae83c3bd2bba4db76efd65e07c11ea3b9}

Accesses (writes) addresses contained in a buffer.

#### Parameters
* `buffer` The buffer 

* `value` The value

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with pointer value type)

#### `public template<>`  <br/>`inline void `[`write`](#structexot_1_1utilities_1_1Evicter_1a5d660a20b6cc3f779680256329ca1d12)`(T address,std::size_t length,volatile T value)` {#structexot_1_1utilities_1_1Evicter_1a5d660a20b6cc3f779680256329ca1d12}

Accesses (writes) addresses using a base pointer and length.

#### Parameters
* `address` The address 

* `length` The length

#### Parameters
* `T` The type 

* `<unnamed>` Template helper (only pointer types)

#### `public template<>`  <br/>`inline void `[`read_in_reverse`](#structexot_1_1utilities_1_1Evicter_1ab0f5851536f8274aa3e3b9205090c7c9)`(T & buffer)` {#structexot_1_1utilities_1_1Evicter_1ab0f5851536f8274aa3e3b9205090c7c9}

Accesses (reads) addresses using a buffer in reverse order.

#### Parameters
* `buffer` The buffer

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with non-pointer value type)

#### `public template<>`  <br/>`inline void `[`read_ptrs_in_reverse`](#structexot_1_1utilities_1_1Evicter_1ac2d844cb429e05ec435894dd5eeb4966)`(T & buffer)` {#structexot_1_1utilities_1_1Evicter_1ac2d844cb429e05ec435894dd5eeb4966}

Accesses (reads) addresses contained in a buffer in reverse order.

#### Parameters
* `buffer` The buffer

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with pointer value type)

#### `public template<>`  <br/>`inline void `[`read_in_reverse`](#structexot_1_1utilities_1_1Evicter_1ab9727b00f423d4173617c7a0543f2607)`(T address,std::size_t length)` {#structexot_1_1utilities_1_1Evicter_1ab9727b00f423d4173617c7a0543f2607}

Accesses (reads) addresses using a base pointer and length in reverse order.

#### Parameters
* `address` The address 

* `length` The length

#### Parameters
* `T` The type 

* `<unnamed>` Template helper (only pointer types)

#### `public template<>`  <br/>`inline void `[`write_in_reverse`](#structexot_1_1utilities_1_1Evicter_1a329576d581ac7886ed919f7dbfdd82ed)`(T & buffer,volatile typename T::value_type value)` {#structexot_1_1utilities_1_1Evicter_1a329576d581ac7886ed919f7dbfdd82ed}

Accesses (writes) addresses using a buffer in reverse order.

#### Parameters
* `buffer` The buffer 

* `value` The value

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with non-pointer value type)

#### `public template<>`  <br/>`inline void `[`write_ptrs_in_reverse`](#structexot_1_1utilities_1_1Evicter_1a1cbc4f7a3be22e6d24f71452b6167b49)`(T & buffer,volatile typename T::value_type value)` {#structexot_1_1utilities_1_1Evicter_1a1cbc4f7a3be22e6d24f71452b6167b49}

Accesses (writes) addresses contained in a buffer in reverse order.

#### Parameters
* `buffer` The buffer 

* `value` The value

#### Parameters
* `T` The type of the buffer 

* `<unnamed>` Template helper (only types with methods `size`, `at,`operator[]`, and with pointer value type)

#### `public template<>`  <br/>`inline void `[`write_in_reverse`](#structexot_1_1utilities_1_1Evicter_1a7a98266803451cae6a8f126b2170d24a)`(T address,std::size_t length,volatile T value)` {#structexot_1_1utilities_1_1Evicter_1a7a98266803451cae6a8f126b2170d24a}

Accesses (writes) addresses using a base pointer and length in reverse order.

#### Parameters
* `address` The address 

* `length` The length 

* `value` The value

#### Parameters
* `T` The type 

* `<unnamed>` Template helper (only pointer types)

# struct `exot::utilities::file_reader` {#structexot_1_1utilities_1_1file__reader}

File reader with raw data access.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  explicit `[`file_reader`](#structexot_1_1utilities_1_1file__reader_1af6828541632e72bc5b0cf2169255cff7)`(std::string && path)` | 
`public inline `[`file_reader`](#structexot_1_1utilities_1_1file__reader)` & `[`operator=`](#structexot_1_1utilities_1_1file__reader_1aa610923d0ba20208d9906be78d761729)`(`[`file_reader`](#structexot_1_1utilities_1_1file__reader)` && other)` | 
`public inline  `[`~file_reader`](#structexot_1_1utilities_1_1file__reader_1a964331f1c6895eb239abb90a26456948)`()` | 
`public template<>`  <br/>`inline auto `[`read_raw`](#structexot_1_1utilities_1_1file__reader_1ad17f7d0455671050822d903b55ccb698)`()` | Read from file into a data type T.
`public template<>`  <br/>`inline auto `[`read_stream`](#structexot_1_1utilities_1_1file__reader_1a68d24fdb37565f6287e00e992dfa9659)`()` | 

## Members

#### `public inline  explicit `[`file_reader`](#structexot_1_1utilities_1_1file__reader_1af6828541632e72bc5b0cf2169255cff7)`(std::string && path)` {#structexot_1_1utilities_1_1file__reader_1af6828541632e72bc5b0cf2169255cff7}

#### `public inline `[`file_reader`](#structexot_1_1utilities_1_1file__reader)` & `[`operator=`](#structexot_1_1utilities_1_1file__reader_1aa610923d0ba20208d9906be78d761729)`(`[`file_reader`](#structexot_1_1utilities_1_1file__reader)` && other)` {#structexot_1_1utilities_1_1file__reader_1aa610923d0ba20208d9906be78d761729}

#### `public inline  `[`~file_reader`](#structexot_1_1utilities_1_1file__reader_1a964331f1c6895eb239abb90a26456948)`()` {#structexot_1_1utilities_1_1file__reader_1a964331f1c6895eb239abb90a26456948}

#### `public template<>`  <br/>`inline auto `[`read_raw`](#structexot_1_1utilities_1_1file__reader_1ad17f7d0455671050822d903b55ccb698)`()` {#structexot_1_1utilities_1_1file__reader_1ad17f7d0455671050822d903b55ccb698}

Read from file into a data type T.

#### Parameters
* `T` The return data type 

* `<unnamed>` Template helper

#### Returns
The read value if successful, nullopt otherwise.

#### `public template<>`  <br/>`inline auto `[`read_stream`](#structexot_1_1utilities_1_1file__reader_1a68d24fdb37565f6287e00e992dfa9659)`()` {#structexot_1_1utilities_1_1file__reader_1a68d24fdb37565f6287e00e992dfa9659}

# struct `exot::utilities::has_input_interface` {#structexot_1_1utilities_1_1has__input__interface}

```
struct exot::utilities::has_input_interface
  : public false_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::has_input_interface< T, std::enable_if_t< is_consumer_v< T > > >` {#structexot_1_1utilities_1_1has__input__interface_3_01T_00_01std_1_1enable__if__t_3_01is__consumer__v_3_01T_01_4_01_4_01_4}

```
struct exot::utilities::has_input_interface< T, std::enable_if_t< is_consumer_v< T > > >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::has_output_interface` {#structexot_1_1utilities_1_1has__output__interface}

```
struct exot::utilities::has_output_interface
  : public false_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::has_output_interface< T, std::enable_if_t< is_producer_v< T > > >` {#structexot_1_1utilities_1_1has__output__interface_3_01T_00_01std_1_1enable__if__t_3_01is__producer__v_3_01T_01_4_01_4_01_4}

```
struct exot::utilities::has_output_interface< T, std::enable_if_t< is_producer_v< T > > >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::has_process_function` {#structexot_1_1utilities_1_1has__process__function}

```
struct exot::utilities::has_process_function
  : public false_type
```  

Type trait to determine if a class has a void(void) process() function.

#### Parameters
* `T` The class 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::has_process_function< T, std::void_t< decltype(std::declval< std::decay_t< T >>().process())> >` {#structexot_1_1utilities_1_1has__process__function_3_01T_00_01std_1_1void__t_3_01decltype_07std_15714445d2f036b890de6592dc077f2b9}

```
struct exot::utilities::has_process_function< T, std::void_t< decltype(std::declval< std::decay_t< T >>().process())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::has_push_back` {#structexot_1_1utilities_1_1has__push__back}

```
struct exot::utilities::has_push_back
  : public false_type
```  

Type trait which determines if a type is CopyInsertable and can be appended to.

#### Parameters
* `T` The type 

* `Enable` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::has_push_back< T, std::void_t< decltype(std::declval< T >().push_back(typename T::value_type{}))> >` {#structexot_1_1utilities_1_1has__push__back_3_01T_00_01std_1_1void__t_3_01decltype_07std_1_1declv5245f06c998069f2b126f35ea4f1fef8}

```
struct exot::utilities::has_push_back< T, std::void_t< decltype(std::declval< T >().push_back(typename T::value_type{}))> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_character` {#structexot_1_1utilities_1_1is__character}

```
struct exot::utilities::is_character
  : public false_type
```  

Type trait for character types.

Enabled if CharT is a standard or wide character.

#### Parameters
* `CharT` The character type 

* `_` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_character< CharT, std::enable_if_t<(std::is_same_v< CharT, char >||std::is_same_v< CharT, wchar_t >||std::is_same_v< CharT, char16_t >||std::is_same_v< CharT, char32_t >)> >` {#structexot_1_1utilities_1_1is__character_3_01CharT_00_01std_1_1enable__if__t_3_07std_1_1is__samea306beda790e2dccea23e978b6b79ee0}

```
struct exot::utilities::is_character< CharT, std::enable_if_t<(std::is_same_v< CharT, char >||std::is_same_v< CharT, wchar_t >||std::is_same_v< CharT, char16_t >||std::is_same_v< CharT, char32_t >)> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_clock` {#structexot_1_1utilities_1_1is__clock}

```
struct exot::utilities::is_clock
  : public false_type
```  

Is the given type a std::chrono-like clock?

#### Parameters
* `T` The type to check 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_clock< T, std::void_t< typename std::decay_t< T >::duration, typename std::decay_t< T >::rep, typename std::decay_t< T >::period, typename std::decay_t< T >::time_point, decltype(std::declval< std::decay_t< T >>().now())> >` {#structexot_1_1utilities_1_1is__clock_3_01T_00_01std_1_1void__t_3_01typename_01std_1_1decay__t_3_e4312b160b30e888b9564072ef7a908d}

```
struct exot::utilities::is_clock< T, std::void_t< typename std::decay_t< T >::duration, typename std::decay_t< T >::rep, typename std::decay_t< T >::period, typename std::decay_t< T >::time_point, decltype(std::declval< std::decay_t< T >>().now())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_comparable` {#structexot_1_1utilities_1_1is__comparable}

```
struct exot::utilities::is_comparable
  : public false_type
```  

Determines if a type is EqualityComparable and LessThanComparable.

#### Parameters
* `T` The type 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_configurable` {#structexot_1_1utilities_1_1is__configurable}

```
struct exot::utilities::is_configurable
  : public false_type
```  

Type trait which determines whether a type has a settings member type, and component and type member functions.

> Todo: This type trait is incomplete (does not detect all required members).

#### Parameters
* `T` The type 

* `_` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_configurable< T, std::enable_if_t< std::is_base_of_v< configurable_base, T > >, std::void_t< decltype(std::declval< std::decay_t< T >>().name()), decltype(std::declval< std::decay_t< T >>().configure())> >` {#structexot_1_1utilities_1_1is__configurable_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base_29e243e6329f5cb3d89eefd6d165e578}

```
struct exot::utilities::is_configurable< T, std::enable_if_t< std::is_base_of_v< configurable_base, T > >, std::void_t< decltype(std::declval< std::decay_t< T >>().name()), decltype(std::declval< std::decay_t< T >>().configure())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_const_iterable` {#structexot_1_1utilities_1_1is__const__iterable}

```
struct exot::utilities::is_const_iterable
  : public false_type
```  

Type trait which determines if a type is const-iterable.

#### Parameters
* `T` The type to check 

* `Enable` A helper template parameter

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_const_iterable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::const_iterator, decltype(std::declval< std::decay_t< T >>().cbegin()), decltype(std::declval< std::decay_t< T >>().cend())> >` {#structexot_1_1utilities_1_1is__const__iterable_3_01T_00_01std_1_1void__t_3_01typename_01std_1_1df2b1a8b7e568c8baec7a29fd9373020b}

```
struct exot::utilities::is_const_iterable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::const_iterator, decltype(std::declval< std::decay_t< T >>().cbegin()), decltype(std::declval< std::decay_t< T >>().cend())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_consumer` {#structexot_1_1utilities_1_1is__consumer}

```
struct exot::utilities::is_consumer
  : public false_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_consumer< T, std::enable_if_t< std::is_base_of_v< exot::framework::TConsumer, std::decay_t< T > > > >` {#structexot_1_1utilities_1_1is__consumer_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base__of_4cc47bb6ffdd352ab2ae390537498f65}

```
struct exot::utilities::is_consumer< T, std::enable_if_t< std::is_base_of_v< exot::framework::TConsumer, std::decay_t< T > > > >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_duration` {#structexot_1_1utilities_1_1is__duration}

```
struct exot::utilities::is_duration
  : public false_type
```  

Is the given type a std::chrono::duration?

#### Parameters
* `T` The type to check

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_duration< std::chrono::duration< Rep, Period > >` {#structexot_1_1utilities_1_1is__duration_3_01std_1_1chrono_1_1duration_3_01Rep_00_01Period_01_4_01_4}

```
struct exot::utilities::is_duration< std::chrono::duration< Rep, Period > >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_equality_comparable` {#structexot_1_1utilities_1_1is__equality__comparable}

```
struct exot::utilities::is_equality_comparable
  : public false_type
```  

Determines if a type is EqualityComparable (named C++ req.)

#### Parameters
* `T` The type 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_equality_comparable< T, std::void_t< decltype(std::declval< T & >()==std::declval< T & >())> >` {#structexot_1_1utilities_1_1is__equality__comparable_3_01T_00_01std_1_1void__t_3_01decltype_07std741eb9cbc46959fd05b2c5296c943610}

```
struct exot::utilities::is_equality_comparable< T, std::void_t< decltype(std::declval< T & >()==std::declval< T & >())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_iterable` {#structexot_1_1utilities_1_1is__iterable}

```
struct exot::utilities::is_iterable
  : public false_type
```  

Type trait which determines if a type satisfies the properties of an iterable type.

#### Parameters
* `T` The type to check 

* `Enable` A helper template parameter

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_iterable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::iterator, decltype(std::declval< std::decay_t< T >>().begin()), decltype(std::declval< std::decay_t< T >>().end())> >` {#structexot_1_1utilities_1_1is__iterable_3_01T_00_01std_1_1void__t_3_01typename_01std_1_1decay__tb7d62002acd7b51abd734987be219ca4}

```
struct exot::utilities::is_iterable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::iterator, decltype(std::declval< std::decay_t< T >>().begin()), decltype(std::declval< std::decay_t< T >>().end())> >
  : public true_type
```  

Valid if the template parameter `std::void_t` is well formed, when all types given to it as parameters are present/valid.

`std::declval` is used to check if class methods exist. `std::decay` removes const/volatile qualifiers, references, giving just the plain type.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_iterable_and_clearable` {#structexot_1_1utilities_1_1is__iterable__and__clearable}

```
struct exot::utilities::is_iterable_and_clearable
  : public false_type
```  

Type trait which determines if a type satisfies the properties of an iterable type.

#### Parameters
* `T` The type to check 

* `Enable` A helper template parameter

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_iterable_and_clearable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::iterator, decltype(std::declval< std::decay_t< T >>().begin()), decltype(std::declval< std::decay_t< T >>().end()), decltype(std::declval< std::decay_t< T >>().clear())> >` {#structexot_1_1utilities_1_1is__iterable__and__clearable_3_01T_00_01std_1_1void__t_3_01typename_050ce63234dcb9bb5a017b625b133f838}

```
struct exot::utilities::is_iterable_and_clearable< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::iterator, decltype(std::declval< std::decay_t< T >>().begin()), decltype(std::declval< std::decay_t< T >>().end()), decltype(std::declval< std::decay_t< T >>().clear())> >
  : public true_type
```  

Valid if the template parameter `std::void_t` is well formed, when all types given to it as parameters are present/valid.

`std::declval` is used to check if class methods exist. `std::decay` removes const/volatile qualifiers, references, giving just the plain type.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_lessthan_comparable` {#structexot_1_1utilities_1_1is__lessthan__comparable}

```
struct exot::utilities::is_lessthan_comparable
  : public false_type
```  

Determines if a type is LessThanComparable (named C++ req.)

#### Parameters
* `T` The type 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_location_accessible` {#structexot_1_1utilities_1_1is__location__accessible}

```
struct exot::utilities::is_location_accessible
  : public false_type
```  

Type trait which determines if a type has some Container facilities: size, and element-wise access.

#### Parameters
* `T` The type to check 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_location_accessible< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::size_type, decltype(std::declval< T & >().size()), decltype(std::declval< T & >().at(std::declval< typename std::decay_t< T >::size_type >())), decltype(std::declval< T & >().operator[](std::declval< typename std::decay_t< T >::size_type >()))> >` {#structexot_1_1utilities_1_1is__location__accessible_3_01T_00_01std_1_1void__t_3_01typename_01stdc23dc2382d8586e616661b7b71cb9e82}

```
struct exot::utilities::is_location_accessible< T, std::void_t< typename std::decay_t< T >::value_type, typename std::decay_t< T >::size_type, decltype(std::declval< T & >().size()), decltype(std::declval< T & >().at(std::declval< typename std::decay_t< T >::size_type >())), decltype(std::declval< T & >().operator[](std::declval< typename std::decay_t< T >::size_type >()))> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_processor` {#structexot_1_1utilities_1_1is__processor}

```
struct exot::utilities::is_processor
  : public false_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_processor< T, std::enable_if_t< std::is_base_of_v< exot::framework::TProcessor, std::decay_t< T > > > >` {#structexot_1_1utilities_1_1is__processor_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base__of77a8540757d0529a68b61d517a22c5e9}

```
struct exot::utilities::is_processor< T, std::enable_if_t< std::is_base_of_v< exot::framework::TProcessor, std::decay_t< T > > > >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_producer` {#structexot_1_1utilities_1_1is__producer}

```
struct exot::utilities::is_producer
  : public false_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_producer< T, std::enable_if_t< std::is_base_of_v< exot::framework::TProducer, std::decay_t< T > > > >` {#structexot_1_1utilities_1_1is__producer_3_01T_00_01std_1_1enable__if__t_3_01std_1_1is__base__of_8d362f8e5e2f19671fbf4255181bbfa7}

```
struct exot::utilities::is_producer< T, std::enable_if_t< std::is_base_of_v< exot::framework::TProducer, std::decay_t< T > > > >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_readable_from_stream` {#structexot_1_1utilities_1_1is__readable__from__stream}

```
struct exot::utilities::is_readable_from_stream
  : public false_type
```  

Determines if a type can be read from an input stream (>>)

#### Parameters
* `T` The type 

* `S` The stream 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_tuple` {#structexot_1_1utilities_1_1is__tuple}

```
struct exot::utilities::is_tuple
  : public exot::utilities::details::is_tuple< std::decay_t< T > >
```  

Type trait which determines if a type is a std::tuple specialisation.

#### Parameters
* `T` The type

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_vector` {#structexot_1_1utilities_1_1is__vector}

```
struct exot::utilities::is_vector
  : public false_type
```  

Type trait which determines if a type is a std::vector.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_vector< std::vector< T, Alloc > >` {#structexot_1_1utilities_1_1is__vector_3_01std_1_1vector_3_01T_00_01Alloc_01_4_01_4}

```
struct exot::utilities::is_vector< std::vector< T, Alloc > >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_writable_to_stream` {#structexot_1_1utilities_1_1is__writable__to__stream}

```
struct exot::utilities::is_writable_to_stream
  : public false_type
```  

Determines if a type can be writen to an output stream (<<)

#### Parameters
* `T` The type 

* `S` The stream 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::larger_of` {#structexot_1_1utilities_1_1larger__of}

```
struct exot::utilities::larger_of
  : public std::conditional<(sizeof(T1) >=sizeof(T2)), T1, T2 >
```  

Provides the larger of two types as a member type.

#### Parameters
* `T1` lhs type 

* `T2` rhs type

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t` {#structexot_1_1utilities_1_1serialised__time__source__t}

The serialised time source.

#### Parameters
* `T` A clock or counter type 

* `Fence` The serialisation type 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Atomic, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1Atomic_698eae7c0917b008e4caa1328f2ffd2d}

```
struct exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Atomic, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >
  : public exot::primitives::fenced_clock< Clock >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Clock, TimingFenceType::None, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1None_006e00cd1f6bbe1b1d274ee9ee7889b31e}

```
struct exot::utilities::serialised_time_source_t< Clock, TimingFenceType::None, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >
  : public exot::primitives::plain_clock< Clock >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Strong, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1Strong_cc90ab1ce53116f24e12bd9aac03e588}

```
struct exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Strong, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >
  : public exot::primitives::__strong_fenced_clock< Clock >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Weak, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Clock_00_01TimingFenceType_1_1Weak_007b5d15101215c09ff525420bfdae3094}

```
struct exot::utilities::serialised_time_source_t< Clock, TimingFenceType::Weak, std::enable_if_t< exot::utilities::is_clock_v< Clock > > >
  : public exot::primitives::__fenced_clock< Clock >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Atomic, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1Atomi0498789b2379c2f53a2ab6c49a3760cf}

```
struct exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Atomic, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >
  : public exot::primitives::fenced_tsc< Counter >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Counter, TimingFenceType::None, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1None_88139d913dbff5f95c56df9630082c61}

```
struct exot::utilities::serialised_time_source_t< Counter, TimingFenceType::None, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >
  : public exot::primitives::plain_tsc< Counter >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Strong, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1Stron5b6ac524cec58840d8831f8e6f69c421}

```
struct exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Strong, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >
  : public exot::primitives::__strong_fenced_tsc< Counter >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Weak, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >` {#structexot_1_1utilities_1_1serialised__time__source__t_3_01Counter_00_01TimingFenceType_1_1Weak_2f687a55c658b3eff2f41dc6d2c82658}

```
struct exot::utilities::serialised_time_source_t< Counter, TimingFenceType::Weak, std::enable_if_t< exot::primitives::is_time_stamp_counter_v< Counter > > >
  : public exot::primitives::__fenced_tsc< Counter >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::smaller_of` {#structexot_1_1utilities_1_1smaller__of}

```
struct exot::utilities::smaller_of
  : public std::conditional<(sizeof(T1) >=sizeof(T2)), T2, T1 >
```  

Provides the smaller of two types as a member type.

#### Parameters
* `T1` lhs type 

* `T2` rhs type

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::synchronised_t` {#structexot_1_1utilities_1_1synchronised__t}

Synchronised type wrapper.

#### Parameters
* `T` The wrapped type

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t_1a853c7e541cf9716b1f4caa6ff605e171)`(const T & object)` | Constructs a synchronised object with const reference.
`public inline  `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t_1a3e4e6e8788de7df88f29df7807140694)`(T && object)` | Constructs a synchronised object with a move (ref or value)
`public inline  `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t_1a432373d61356547c35401b85c1b65698)`(const `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & other)` | Constructs a synchronised object by copying.
`public inline `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & `[`operator=`](#structexot_1_1utilities_1_1synchronised__t_1a92a22d63dc168bed346061ff0fc80c51)`(const `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & other)` | Assigns wrapped contents from another passed by const ref.
`public inline `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & `[`operator=`](#structexot_1_1utilities_1_1synchronised__t_1a283a3dea27e1cddcd492ba410afe7c98)`(`[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & other)` | Assigns wrapped contents from another passed by 'mutable' ref.
`public template<>`  <br/>`inline auto `[`access`](#structexot_1_1utilities_1_1synchronised__t_1a9773749c197195df5239cc4973deb18b)`(Callable && callable)` | Accesses the wrapped contents while holding a lock using a callable.
`public inline wrapped_type * `[`operator->`](#structexot_1_1utilities_1_1synchronised__t_1a78ffa8ffee7ac0adf404f3a1969b51ee)`()` | 
`public inline wrapped_type * `[`operator&`](#structexot_1_1utilities_1_1synchronised__t_1a8e3bf4fb1ba179f9dfa7b20179e2ac09)`()` | 
`public inline wrapped_type & `[`operator*`](#structexot_1_1utilities_1_1synchronised__t_1a679dd3c465e497e6221ea7fa21050a7f)`()` | 
`public inline  `[`operator wrapped_type`](#structexot_1_1utilities_1_1synchronised__t_1a25257f53c77136f9033dafe351a62ff6)`() const` | 
`typedef `[`wrapped_type`](#structexot_1_1utilities_1_1synchronised__t_1a714085b17ac3d942ebebdbfefce46010) | 
`typedef `[`lock_type`](#structexot_1_1utilities_1_1synchronised__t_1aee74b7f18224d36a6a2da1803f384a6b) | 
`typedef `[`guard_type`](#structexot_1_1utilities_1_1synchronised__t_1a28a18e0f1819ea1ceba7c81476e4e3d5) | 

## Members

#### `public inline  `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t_1a853c7e541cf9716b1f4caa6ff605e171)`(const T & object)` {#structexot_1_1utilities_1_1synchronised__t_1a853c7e541cf9716b1f4caa6ff605e171}

Constructs a synchronised object with const reference.

#### Parameters
* `object` The object

#### `public inline  `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t_1a3e4e6e8788de7df88f29df7807140694)`(T && object)` {#structexot_1_1utilities_1_1synchronised__t_1a3e4e6e8788de7df88f29df7807140694}

Constructs a synchronised object with a move (ref or value)

#### Parameters
* `object` The object

#### `public inline  `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t_1a432373d61356547c35401b85c1b65698)`(const `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & other)` {#structexot_1_1utilities_1_1synchronised__t_1a432373d61356547c35401b85c1b65698}

Constructs a synchronised object by copying.

#### Parameters
* `other` The other

#### `public inline `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & `[`operator=`](#structexot_1_1utilities_1_1synchronised__t_1a92a22d63dc168bed346061ff0fc80c51)`(const `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & other)` {#structexot_1_1utilities_1_1synchronised__t_1a92a22d63dc168bed346061ff0fc80c51}

Assigns wrapped contents from another passed by const ref.

#### Parameters
* `other` The other

#### Returns
The reference to the updated object

#### `public inline `[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & `[`operator=`](#structexot_1_1utilities_1_1synchronised__t_1a283a3dea27e1cddcd492ba410afe7c98)`(`[`synchronised_t`](#structexot_1_1utilities_1_1synchronised__t)` & other)` {#structexot_1_1utilities_1_1synchronised__t_1a283a3dea27e1cddcd492ba410afe7c98}

Assigns wrapped contents from another passed by 'mutable' ref.

#### Parameters
* `other` The other

#### Returns
The reference to the updated object

#### `public template<>`  <br/>`inline auto `[`access`](#structexot_1_1utilities_1_1synchronised__t_1a9773749c197195df5239cc4973deb18b)`(Callable && callable)` {#structexot_1_1utilities_1_1synchronised__t_1a9773749c197195df5239cc4973deb18b}

Accesses the wrapped contents while holding a lock using a callable.

#### Parameters
* `callable` The callable

#### Parameters
* `Callable` The type of the callable

#### Returns
The return value of the callable

#### `public inline wrapped_type * `[`operator->`](#structexot_1_1utilities_1_1synchronised__t_1a78ffa8ffee7ac0adf404f3a1969b51ee)`()` {#structexot_1_1utilities_1_1synchronised__t_1a78ffa8ffee7ac0adf404f3a1969b51ee}

#### `public inline wrapped_type * `[`operator&`](#structexot_1_1utilities_1_1synchronised__t_1a8e3bf4fb1ba179f9dfa7b20179e2ac09)`()` {#structexot_1_1utilities_1_1synchronised__t_1a8e3bf4fb1ba179f9dfa7b20179e2ac09}

#### `public inline wrapped_type & `[`operator*`](#structexot_1_1utilities_1_1synchronised__t_1a679dd3c465e497e6221ea7fa21050a7f)`()` {#structexot_1_1utilities_1_1synchronised__t_1a679dd3c465e497e6221ea7fa21050a7f}

#### `public inline  `[`operator wrapped_type`](#structexot_1_1utilities_1_1synchronised__t_1a25257f53c77136f9033dafe351a62ff6)`() const` {#structexot_1_1utilities_1_1synchronised__t_1a25257f53c77136f9033dafe351a62ff6}

#### `typedef `[`wrapped_type`](#structexot_1_1utilities_1_1synchronised__t_1a714085b17ac3d942ebebdbfefce46010) {#structexot_1_1utilities_1_1synchronised__t_1a714085b17ac3d942ebebdbfefce46010}

#### `typedef `[`lock_type`](#structexot_1_1utilities_1_1synchronised__t_1aee74b7f18224d36a6a2da1803f384a6b) {#structexot_1_1utilities_1_1synchronised__t_1aee74b7f18224d36a6a2da1803f384a6b}

#### `typedef `[`guard_type`](#structexot_1_1utilities_1_1synchronised__t_1a28a18e0f1819ea1ceba7c81476e4e3d5) {#structexot_1_1utilities_1_1synchronised__t_1a28a18e0f1819ea1ceba7c81476e4e3d5}

# struct `exot::utilities::ThreadTraits` {#structexot_1_1utilities_1_1ThreadTraits}

A class that holds static methods to set thread properties.

May have no effect on certain platforms. The functions are arranged in a class such that it can potentially be used, for example, as a template parameter, injecting behaviour in other classes.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::time_source_t` {#structexot_1_1utilities_1_1time__source__t}

The time source type, a clock or a counter.

#### Parameters
* `Source` The timing source type

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::time_source_t< TimingSourceType::HardwarePerformanceCounter >` {#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1HardwarePerformanceCounter_01_4}

```
struct exot::utilities::time_source_t< TimingSourceType::HardwarePerformanceCounter >
  : public perf_clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::time_source_t< TimingSourceType::MonotonicClock >` {#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1MonotonicClock_01_4}

```
struct exot::utilities::time_source_t< TimingSourceType::MonotonicClock >
  : public monotonic_clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::time_source_t< TimingSourceType::MonotonicCounter >` {#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1MonotonicCounter_01_4}

```
struct exot::utilities::time_source_t< TimingSourceType::MonotonicCounter >
  : public MonotonicCounter
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::time_source_t< TimingSourceType::SoftwarePerformanceCounter >` {#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1SoftwarePerformanceCounter_01_4}

```
struct exot::utilities::time_source_t< TimingSourceType::SoftwarePerformanceCounter >
  : public perf_sw_clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::time_source_t< TimingSourceType::SteadyClock >` {#structexot_1_1utilities_1_1time__source__t_3_01TimingSourceType_1_1SteadyClock_01_4}

```
struct exot::utilities::time_source_t< TimingSourceType::SteadyClock >
  : public steady_clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_lessthan_comparable< T, std::void_t< decltype(std::declval< T & >()< std::declval< T & >())> >` {#structexot_1_1utilities_1_1is__lessthan__comparable_3_01T_00_01std_1_1void__t_3_01decltype_07stdb0a26240cd828af3e2e34ed0f506bb5e}

```
struct exot::utilities::is_lessthan_comparable< T, std::void_t< decltype(std::declval< T & >()< std::declval< T & >())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::is_comparable< T, std::void_t< decltype(std::declval< T & >()==std::declval< T & >()), decltype(std::declval< T & >()< std::declval< T & >())> >` {#structexot_1_1utilities_1_1is__comparable_3_01T_00_01std_1_1void__t_3_01decltype_07std_1_1declva291e77fcf2c740f79acc0eb5ffe579f8}

```
struct exot::utilities::is_comparable< T, std::void_t< decltype(std::declval< T & >()==std::declval< T & >()), decltype(std::declval< T & >()< std::declval< T & >())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::utilities::details` {#namespaceexot_1_1utilities_1_1details}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public template<>`  <br/>`constexpr void `[`const_for_impl`](#helpers_8h_1afd24720422689765dade4b4606582b34)`(Callable && func,std::index_sequence< I... >)`            | Helper template used by `const_for`
`public template<>`  <br/>`constexpr void `[`for_each_impl`](#helpers_8h_1a51e4a90d0befe046e7ca2838fcb92660)`(Tuple && tuple,Callable && func,std::index_sequence< I... >)`            | Helper template used by `for_each`
`public template<>`  <br/>`auto `[`zip_at_idx`](#helpers_8h_1a85f517f46d86b8f304383891af8ba1ce)`(Ts &&... ts)`            | Makes a tuple out of values of tuples at a specific index position.
`public template<>`  <br/>`auto `[`zip_impl`](#helpers_8h_1ac6f7fcc70e50062b659bec1278dfa7b2)`(Ts &&... ts,std::index_sequence< I... >)`            | Zips a number of tuples.
`public template<>`  <br/>`auto `[`zip_fwd_at_idx`](#helpers_8h_1a4fa90226eae5297a9bb5c989e488969c)`(Ts &&... ts)`            | Makes a tuple with forwarded values of tuples at specific index.
`public template<>`  <br/>`auto `[`zip_fwd_impl`](#helpers_8h_1a97d7d0181bcc539c221593e831763941)`(Ts &&... ts,std::index_sequence< I... >)`            | Zips a number of tuples by forwarding values.
`public template<>`  <br/>`auto `[`slice_tuple`](#helpers_8h_1a2ae042cb614acb6bff130061399ebd9d)`(std::tuple< Ts... > && _t,std::index_sequence< Is... >)`            | 
`public template<>`  <br/>`auto `[`slice_fwd_tuple`](#helpers_8h_1a1d8c21a38194224937356d03dc1dcf47)`(std::tuple< Ts... > && _t,std::index_sequence< Is... >)`            | 
`public template<>`  <br/>`inline std::basic_istringstream< CharT > `[`read_into_stringstream`](#istream_8h_1a72f02fd7f6a8166b8370811db470c993)`(std::basic_istream< CharT, CharTraitsT > & stream)`            | Reads a token from an input stream into a input stringstream.
`public template<>`  <br/>`auto `[`chrono_statistics`](#timing_8h_1ab06fbd85340125199720640a703784ac)`(const std::vector< InputGranularity > & input)`            | Computes mean and standard deviation from a vector of std::chrono::duration.
`struct `[`exot::utilities::details::get_overhead`](#structexot_1_1utilities_1_1details_1_1get__overhead) | Functor to estimate the mean overhead for basic timing primitives.
`struct `[`exot::utilities::details::is_tuple`](#structexot_1_1utilities_1_1details_1_1is__tuple) | Type trait which determines if a type is a std::tuple.
`struct `[`exot::utilities::details::is_tuple< std::tuple< Types... > >`](#structexot_1_1utilities_1_1details_1_1is__tuple_3_01std_1_1tuple_3_01Types_8_8_8_01_4_01_4) | #### Parameters
`struct `[`exot::utilities::details::Separators`](#structexot_1_1utilities_1_1details_1_1Separators) | Prefix, postfix, and delimeter used in serialising ranges.
`struct `[`exot::utilities::details::Separators< CharT, T, typename std::enable_if_t< is_const_iterable_v< T > >::value >`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282) | 
`struct `[`exot::utilities::details::Separators< CharT, T, typename std::enable_if_t< is_iterable_v< T > >::value >`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e) | 
`struct `[`exot::utilities::details::Separators< CharT, T, typename std::enable_if_t< is_tuple_v< T > >::value >`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00) | 
`struct `[`exot::utilities::details::sleep_overhead`](#structexot_1_1utilities_1_1details_1_1sleep__overhead) | Functor to estimate the overhead of the sleeping function.
`struct `[`exot::utilities::details::TimeKeeperOptions`](#structexot_1_1utilities_1_1details_1_1TimeKeeperOptions) | 
`struct `[`exot::utilities::details::timing_overhead`](#structexot_1_1utilities_1_1details_1_1timing__overhead) | Functor to estimate the overhead of the basic timing primitives.

## Members

#### `public template<>`  <br/>`constexpr void `[`const_for_impl`](#helpers_8h_1afd24720422689765dade4b4606582b34)`(Callable && func,std::index_sequence< I... >)` {#helpers_8h_1afd24720422689765dade4b4606582b34}

Helper template used by `const_for`

The helper uses pack expansion to construct a compile-time sequence of `std::size_t` integers, which are then incrementally provided to a callable object, also by means of parameter pack expansion.

`std::size_t` is used because it is commonly used for array indexing and loop counting. Moreover, this allows the use of the `sizeof` operator, which return type is `size_t`.

#### Parameters
* `func` A callable object (e.g. lambda, functor) 

* `<unnamed>` A compile-time sequence of `std::size_t` integers, used in template pack expansion

#### Parameters
* `Begin` First sequence number (similar to the first parameter in a `for` loop declaration) 

* `Callable` A callable type 

* `I` Sequence of `std::size_t` types

#### `public template<>`  <br/>`constexpr void `[`for_each_impl`](#helpers_8h_1a51e4a90d0befe046e7ca2838fcb92660)`(Tuple && tuple,Callable && func,std::index_sequence< I... >)` {#helpers_8h_1a51e4a90d0befe046e7ca2838fcb92660}

Helper template used by `for_each`

The helper uses a compile-time sequence of integers and pack expansion to access tuple elements via `std::get`.

#### Parameters
* `tuple` A tuple 

* `func` A callable object 

* `<unnamed>` A compile-time sequence of `std::size_t` integers, used in template pack expansion

#### Parameters
* `Callable` A callable type 

* `Tuple` The type of the tuple 

* `I` Sequence of `std::size_t` types

#### `public template<>`  <br/>`auto `[`zip_at_idx`](#helpers_8h_1a85f517f46d86b8f304383891af8ba1ce)`(Ts &&... ts)` {#helpers_8h_1a85f517f46d86b8f304383891af8ba1ce}

Makes a tuple out of values of tuples at a specific index position.

#### Parameters
* `I` The index 

* `Ts` The tuples' types 

#### Parameters
* `ts` The tuples 

#### Returns
A tuple of values at position I

#### `public template<>`  <br/>`auto `[`zip_impl`](#helpers_8h_1ac6f7fcc70e50062b659bec1278dfa7b2)`(Ts &&... ts,std::index_sequence< I... >)` {#helpers_8h_1ac6f7fcc70e50062b659bec1278dfa7b2}

Zips a number of tuples.

#### Parameters
* `Ts` The tuples' types 

* `I` The index sequence 

#### Parameters
* `ts` The tuples 

#### Returns
The zipped tupples, a tuple of tuples

#### `public template<>`  <br/>`auto `[`zip_fwd_at_idx`](#helpers_8h_1a4fa90226eae5297a9bb5c989e488969c)`(Ts &&... ts)` {#helpers_8h_1a4fa90226eae5297a9bb5c989e488969c}

Makes a tuple with forwarded values of tuples at specific index.

#### Parameters
* `I` The index 

* `Ts` The tuples' types 

#### Parameters
* `ts` The tuples 

#### Returns
A tuple with forwarded values

#### `public template<>`  <br/>`auto `[`zip_fwd_impl`](#helpers_8h_1a97d7d0181bcc539c221593e831763941)`(Ts &&... ts,std::index_sequence< I... >)` {#helpers_8h_1a97d7d0181bcc539c221593e831763941}

Zips a number of tuples by forwarding values.

#### Parameters
* `Ts` The tuples' types 

* `I` The index sequence 

#### Parameters
* `ts` The tuples 

#### Returns
The zipped tupples, a tuple of tuples

#### `public template<>`  <br/>`auto `[`slice_tuple`](#helpers_8h_1a2ae042cb614acb6bff130061399ebd9d)`(std::tuple< Ts... > && _t,std::index_sequence< Is... >)` {#helpers_8h_1a2ae042cb614acb6bff130061399ebd9d}

#### `public template<>`  <br/>`auto `[`slice_fwd_tuple`](#helpers_8h_1a1d8c21a38194224937356d03dc1dcf47)`(std::tuple< Ts... > && _t,std::index_sequence< Is... >)` {#helpers_8h_1a1d8c21a38194224937356d03dc1dcf47}

#### `public template<>`  <br/>`inline std::basic_istringstream< CharT > `[`read_into_stringstream`](#istream_8h_1a72f02fd7f6a8166b8370811db470c993)`(std::basic_istream< CharT, CharTraitsT > & stream)` {#istream_8h_1a72f02fd7f6a8166b8370811db470c993}

Reads a token from an input stream into a input stringstream.

#### Parameters
* `stream` The input stream

#### Parameters
* `CharT` Character type used by the stream 

* `CharTraitsT` Character traits used by the stream

#### Returns
A single token as a stringstream

#### `public template<>`  <br/>`auto `[`chrono_statistics`](#timing_8h_1ab06fbd85340125199720640a703784ac)`(const std::vector< InputGranularity > & input)` {#timing_8h_1ab06fbd85340125199720640a703784ac}

Computes mean and standard deviation from a vector of std::chrono::duration.

#### Parameters
* `input` Input vector of InputGranularity objects.

#### Parameters
* `InputGranularity` Input duration granularity used in the vector, e.g. `std::chrono::nanoseconds`; 

* `OutputGranularity` Output duration granularity;

#### Returns
Tuple holding computed mean and standard deviation.

# struct `exot::utilities::details::get_overhead` {#structexot_1_1utilities_1_1details_1_1get__overhead}

Functor to estimate the mean overhead for basic timing primitives.

#### Parameters
* `Clock` Evaluated clock type, e.g. std::chrono::steady_clock; 

* `Overhead` The particular overhead functor

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline duration_type `[`operator()`](#structexot_1_1utilities_1_1details_1_1get__overhead_1aabf0953304dd563972c9ca4209edd104)`(unsigned int iterations)` | Repetitively calls [timing_overhead](#structexot_1_1utilities_1_1details_1_1timing__overhead).
`typedef `[`clock_type`](#structexot_1_1utilities_1_1details_1_1get__overhead_1a68bbc58469ac007ee9765744cdfa50bb) | 
`typedef `[`duration_type`](#structexot_1_1utilities_1_1details_1_1get__overhead_1a61b33d5d748e8d9285e5cde883c29312) | 
`typedef `[`overhead`](#structexot_1_1utilities_1_1details_1_1get__overhead_1ad767dd95df93e1c37c311c54d706c87d) | 

## Members

#### `public inline duration_type `[`operator()`](#structexot_1_1utilities_1_1details_1_1get__overhead_1aabf0953304dd563972c9ca4209edd104)`(unsigned int iterations)` {#structexot_1_1utilities_1_1details_1_1get__overhead_1aabf0953304dd563972c9ca4209edd104}

Repetitively calls [timing_overhead](#structexot_1_1utilities_1_1details_1_1timing__overhead).

#### Parameters
* `iterations` Number of repeated calls to [timing_overhead](#structexot_1_1utilities_1_1details_1_1timing__overhead). 

#### Returns
Mean timing overhead over all iterations.

#### `typedef `[`clock_type`](#structexot_1_1utilities_1_1details_1_1get__overhead_1a68bbc58469ac007ee9765744cdfa50bb) {#structexot_1_1utilities_1_1details_1_1get__overhead_1a68bbc58469ac007ee9765744cdfa50bb}

#### `typedef `[`duration_type`](#structexot_1_1utilities_1_1details_1_1get__overhead_1a61b33d5d748e8d9285e5cde883c29312) {#structexot_1_1utilities_1_1details_1_1get__overhead_1a61b33d5d748e8d9285e5cde883c29312}

#### `typedef `[`overhead`](#structexot_1_1utilities_1_1details_1_1get__overhead_1ad767dd95df93e1c37c311c54d706c87d) {#structexot_1_1utilities_1_1details_1_1get__overhead_1ad767dd95df93e1c37c311c54d706c87d}

# struct `exot::utilities::details::is_tuple` {#structexot_1_1utilities_1_1details_1_1is__tuple}

```
struct exot::utilities::details::is_tuple
  : public false_type
```  

Type trait which determines if a type is a std::tuple.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::details::is_tuple< std::tuple< Types... > >` {#structexot_1_1utilities_1_1details_1_1is__tuple_3_01std_1_1tuple_3_01Types_8_8_8_01_4_01_4}

```
struct exot::utilities::details::is_tuple< std::tuple< Types... > >
  : public true_type
```  

#### Parameters
* `Types` A parameter pack of types used in a tuple. Matches any valid `std::tuple`.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::details::Separators` {#structexot_1_1utilities_1_1details_1_1Separators}

Prefix, postfix, and delimeter used in serialising ranges.

Characters can be chosen individually for different types, using the type trait functions from <type_traits> or "types.h".

#### Parameters
* `CharT` Character type (e.g. char, wchar_t) 

* `T` Range type 

* `Enable` Used for `std::enable_if`-based polymorphism

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_1a80a73392ab6167c5533fdf901f16bfa9) | 
`public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_1a8c3de15771e5924227fec1912859c5c5) | 
`public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_1a1cae4f62266d3c5ec12517ffd338ed2a) | 
`public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_1ae12bcf3d3c9735b6d38e73f9ebec6694)`()` | 

## Members

#### `public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_1a80a73392ab6167c5533fdf901f16bfa9) {#structexot_1_1utilities_1_1details_1_1Separators_1a80a73392ab6167c5533fdf901f16bfa9}

#### `public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_1a8c3de15771e5924227fec1912859c5c5) {#structexot_1_1utilities_1_1details_1_1Separators_1a8c3de15771e5924227fec1912859c5c5}

#### `public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_1a1cae4f62266d3c5ec12517ffd338ed2a) {#structexot_1_1utilities_1_1details_1_1Separators_1a1cae4f62266d3c5ec12517ffd338ed2a}

#### `public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_1ae12bcf3d3c9735b6d38e73f9ebec6694)`()` {#structexot_1_1utilities_1_1details_1_1Separators_1ae12bcf3d3c9735b6d38e73f9ebec6694}

# struct `exot::utilities::details::Separators< CharT, T, typename std::enable_if_t< is_const_iterable_v< T > >::value >` {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a5224e93c7f96227c89b2523a6ac4cfa9) | 
`public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1afa1c7dcc54b7b67877015440b194b74f) | 
`public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a3efa98b974d2743fc3513638b372bfd8) | 
`public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a01949ca512c97cf712a39277d66b446d)`()` | 

## Members

#### `public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a5224e93c7f96227c89b2523a6ac4cfa9) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a5224e93c7f96227c89b2523a6ac4cfa9}

#### `public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1afa1c7dcc54b7b67877015440b194b74f) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1afa1c7dcc54b7b67877015440b194b74f}

#### `public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a3efa98b974d2743fc3513638b372bfd8) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a3efa98b974d2743fc3513638b372bfd8}

#### `public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a01949ca512c97cf712a39277d66b446d)`()` {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_15ac8d6de69ead7e3cc7aabaec3b3282_1a01949ca512c97cf712a39277d66b446d}

# struct `exot::utilities::details::Separators< CharT, T, typename std::enable_if_t< is_iterable_v< T > >::value >` {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a7d9d07c1bca2c10e427f05a1c048091c) | 
`public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1aa8ff25d67a673a2e8b62b5a5bd225866) | 
`public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a0abe00408d4e0f0f1fc1fca890b12f09) | 
`public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a50961965bbc6e823a0946a77f2feb353)`()` | 

## Members

#### `public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a7d9d07c1bca2c10e427f05a1c048091c) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a7d9d07c1bca2c10e427f05a1c048091c}

#### `public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1aa8ff25d67a673a2e8b62b5a5bd225866) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1aa8ff25d67a673a2e8b62b5a5bd225866}

#### `public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a0abe00408d4e0f0f1fc1fca890b12f09) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a0abe00408d4e0f0f1fc1fca890b12f09}

#### `public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a50961965bbc6e823a0946a77f2feb353)`()` {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_c4f16f40c69ffd4d5a6c5c9d5551b13e_1a50961965bbc6e823a0946a77f2feb353}

# struct `exot::utilities::details::Separators< CharT, T, typename std::enable_if_t< is_tuple_v< T > >::value >` {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a973ea21bde9dbaa5c140c04bcc508a35) | 
`public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a44fc30cd28009f141a3555fbabf96f4b) | 
`public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a9837c6481e1e8e11486a87e924e2fe6f) | 
`public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a7ab4ba8a9d2fdd80e015cc1dc9da4dfb)`()` | 

## Members

#### `public const CharT `[`prefix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a973ea21bde9dbaa5c140c04bcc508a35) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a973ea21bde9dbaa5c140c04bcc508a35}

#### `public const CharT `[`postfix`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a44fc30cd28009f141a3555fbabf96f4b) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a44fc30cd28009f141a3555fbabf96f4b}

#### `public const CharT `[`delimeter`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a9837c6481e1e8e11486a87e924e2fe6f) {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a9837c6481e1e8e11486a87e924e2fe6f}

#### `public inline constexpr `[`Separators`](#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a7ab4ba8a9d2fdd80e015cc1dc9da4dfb)`()` {#structexot_1_1utilities_1_1details_1_1Separators_3_01CharT_00_01T_00_01typename_01std_1_1enable_2e1b2dd229034b73e7477cd875eabd00_1a7ab4ba8a9d2fdd80e015cc1dc9da4dfb}

# struct `exot::utilities::details::sleep_overhead` {#structexot_1_1utilities_1_1details_1_1sleep__overhead}

Functor to estimate the overhead of the sleeping function.

#### Parameters
* `Clock` Evaluated clock type, e.g. std::chrono::steady_clock;

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  explicit `[`sleep_overhead`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab6a55e813828dddf65d84255a77fa180)`(duration_type duration)` | Constructor that sets the sleep duration.
`public inline  `[`sleep_overhead`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab05930eb20be76aa57fdd19ad0322e29)`()` | The default constructor, estimate the overhead of calling the sleep function with zero sleep duration.
`public inline duration_type `[`operator()`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab5594520029306cb0ff7ef365f46f9f1)`()` | 
`typedef `[`clock_type`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ae6ea902e8db93bf8bc404f60207dfa88) | 
`typedef `[`duration_type`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1a9ba03f9939c3dba40055255e124abdf2) | 

## Members

#### `public inline  explicit `[`sleep_overhead`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab6a55e813828dddf65d84255a77fa180)`(duration_type duration)` {#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab6a55e813828dddf65d84255a77fa180}

Constructor that sets the sleep duration.

#### Parameters
* `duration` The sleep duration

#### `public inline  `[`sleep_overhead`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab05930eb20be76aa57fdd19ad0322e29)`()` {#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab05930eb20be76aa57fdd19ad0322e29}

The default constructor, estimate the overhead of calling the sleep function with zero sleep duration.

#### `public inline duration_type `[`operator()`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab5594520029306cb0ff7ef365f46f9f1)`()` {#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ab5594520029306cb0ff7ef365f46f9f1}

#### `typedef `[`clock_type`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ae6ea902e8db93bf8bc404f60207dfa88) {#structexot_1_1utilities_1_1details_1_1sleep__overhead_1ae6ea902e8db93bf8bc404f60207dfa88}

#### `typedef `[`duration_type`](#structexot_1_1utilities_1_1details_1_1sleep__overhead_1a9ba03f9939c3dba40055255e124abdf2) {#structexot_1_1utilities_1_1details_1_1sleep__overhead_1a9ba03f9939c3dba40055255e124abdf2}

# struct `exot::utilities::details::TimeKeeperOptions` {#structexot_1_1utilities_1_1details_1_1TimeKeeperOptions}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::details::timing_overhead` {#structexot_1_1utilities_1_1details_1_1timing__overhead}

Functor to estimate the overhead of the basic timing primitives.

#### Parameters
* `Clock` Evaluated clock type, e.g. std::chrono::steady_clock;

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline duration_type `[`operator()`](#structexot_1_1utilities_1_1details_1_1timing__overhead_1af27ae50a93ca7bb04c8c83e96062a832)`()` | #### Returns
`typedef `[`clock_type`](#structexot_1_1utilities_1_1details_1_1timing__overhead_1ae729d505082ca3b878110b36b4fbc338) | 
`typedef `[`duration_type`](#structexot_1_1utilities_1_1details_1_1timing__overhead_1a31f479782e818f4a7b2aa0efb7464bbd) | 

## Members

#### `public inline duration_type `[`operator()`](#structexot_1_1utilities_1_1details_1_1timing__overhead_1af27ae50a93ca7bb04c8c83e96062a832)`()` {#structexot_1_1utilities_1_1details_1_1timing__overhead_1af27ae50a93ca7bb04c8c83e96062a832}

#### Returns
Time difference between the consecutive calls to now().

#### `typedef `[`clock_type`](#structexot_1_1utilities_1_1details_1_1timing__overhead_1ae729d505082ca3b878110b36b4fbc338) {#structexot_1_1utilities_1_1details_1_1timing__overhead_1ae729d505082ca3b878110b36b4fbc338}

#### `typedef `[`duration_type`](#structexot_1_1utilities_1_1details_1_1timing__overhead_1a31f479782e818f4a7b2aa0efb7464bbd) {#structexot_1_1utilities_1_1details_1_1timing__overhead_1a31f479782e818f4a7b2aa0efb7464bbd}

# namespace `exot::utilities::is_readable_from_stream std` {#namespaceexot_1_1utilities_1_1is__readable__from__stream_01std}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[`exot::utilities::is_readable_from_stream std::declval< T & >())> >`](#structexot_1_1utilities_1_1is__readable__from__stream_01std_1_1declval_3_01T_01_6_01_4_07_08_08_4_01_4) | 

# struct `exot::utilities::is_readable_from_stream std::declval< T & >())> >` {#structexot_1_1utilities_1_1is__readable__from__stream_01std_1_1declval_3_01T_01_6_01_4_07_08_08_4_01_4}

```
struct exot::utilities::is_readable_from_stream std::declval< T & >())> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::utilities::workers` {#namespaceexot_1_1utilities_1_1workers}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::utilities::workers::TemplatedWorker`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker) | Class for templated worker, which uses policy-based design.
`struct `[`exot::utilities::workers::BarrierWorker`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker) | Synchronised worker with barriers.
`struct `[`exot::utilities::workers::PinnedBarrierWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker) | Synchronised worker with barriers.
`struct `[`exot::utilities::workers::PinnedWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker) | [Worker](#structexot_1_1utilities_1_1workers_1_1Worker) with custom thread properties.
`struct `[`exot::utilities::workers::Worker`](#structexot_1_1utilities_1_1workers_1_1Worker) | Basic worker.

# class `exot::utilities::workers::TemplatedWorker` {#classexot_1_1utilities_1_1workers_1_1TemplatedWorker}

```
class exot::utilities::workers::TemplatedWorker
  : public SynchronisationPolicy
  : public ThreadingPolicy
  : public SynchronisationPolicy
  : public ThreadingPolicy
```  

Class for templated worker, which uses policy-based design.

Uses one of the mixin classes above to provide additional functionality.

#### Parameters
* `SynchronisationPolicy` A synchronisation mixin class type 

* `ThreadingPolicy` A threading policy mixin class type

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline  `[`TemplatedWorker`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a7d8bd16522993b7b2e6bf22dcf6d67aa)`(state_pointer state,typename SynchronisationPolicy::Configuration && synch,typename ThreadingPolicy::Configuration && thread,work_type && work,logger_pointer logger)` | Constructs the templated worker.
`public inline void `[`operator()`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a35dcef259f7aa8bfecabfe81338c278c)`()` | 
`typedef `[`state_pointer`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a0cf6d5132b561c5bc6931fd351d6a26d) | 
`typedef `[`logger_pointer`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1ae1b2ee24e5e54e3a688131ecc65469c6) | 
`typedef `[`work_type`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a1ba6636617ec8013d5f2ed9b023ba4aa) | 

## Members

#### `public inline  `[`TemplatedWorker`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a7d8bd16522993b7b2e6bf22dcf6d67aa)`(state_pointer state,typename SynchronisationPolicy::Configuration && synch,typename ThreadingPolicy::Configuration && thread,work_type && work,logger_pointer logger)` {#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a7d8bd16522993b7b2e6bf22dcf6d67aa}

Constructs the templated worker.

#### Parameters
* `state` A pointer to a state object 

* `synch` Synchronisation configuration 

* `thread.` Threading configuration 

* `work` The callable work object 

* `logger` A pointer to a debug logger

#### `public inline void `[`operator()`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a35dcef259f7aa8bfecabfe81338c278c)`()` {#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a35dcef259f7aa8bfecabfe81338c278c}

#### `typedef `[`state_pointer`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a0cf6d5132b561c5bc6931fd351d6a26d) {#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a0cf6d5132b561c5bc6931fd351d6a26d}

#### `typedef `[`logger_pointer`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1ae1b2ee24e5e54e3a688131ecc65469c6) {#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1ae1b2ee24e5e54e3a688131ecc65469c6}

#### `typedef `[`work_type`](#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a1ba6636617ec8013d5f2ed9b023ba4aa) {#classexot_1_1utilities_1_1workers_1_1TemplatedWorker_1a1ba6636617ec8013d5f2ed9b023ba4aa}

# struct `exot::utilities::workers::BarrierWorker` {#structexot_1_1utilities_1_1workers_1_1BarrierWorker}

Synchronised worker with barriers.

The work function is performed between two barriers.

#### Parameters
* `Work` A callable object of signature void()

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`BarrierWorker`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a5bf440afa0d087bb1a3af169056d2f61)`() = delete` | No default constructor
`public inline  `[`BarrierWorker`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a8b44cc96465eab9b11cc6aa81234d6b2)`(state_pointer state,barrier_type & barrier,work_type && work,logger_pointer logger)` | Constructor for the barrier worker.
`public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1ab59fb1fdeb7a38f388610af3d5dfc953)`()` | Main operation.
`typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1ac7323854d2947ea1866aa982c6a810f1) | 
`typedef `[`barrier_type`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a519b8a58d634736b1cc1d4484aecdddf) | 
`typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a409c6fbd6804e1fe800dd4389ed2a033) | 
`typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a7ad6f50255ec720ea57b2ecc875104c0) | 

## Members

#### `public  `[`BarrierWorker`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a5bf440afa0d087bb1a3af169056d2f61)`() = delete` {#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a5bf440afa0d087bb1a3af169056d2f61}

No default constructor

#### `public inline  `[`BarrierWorker`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a8b44cc96465eab9b11cc6aa81234d6b2)`(state_pointer state,barrier_type & barrier,work_type && work,logger_pointer logger)` {#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a8b44cc96465eab9b11cc6aa81234d6b2}

Constructor for the barrier worker.

#### Parameters
* `state` The pointer to a state object 

* `barrier` The reference to a barrier object 

* `logger` A pointer to a debug logger 

* `work` A callable object

#### `public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1ab59fb1fdeb7a38f388610af3d5dfc953)`()` {#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1ab59fb1fdeb7a38f388610af3d5dfc953}

Main operation.

#### Parameters
* `barrier` A reference to a barrier

#### `typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1ac7323854d2947ea1866aa982c6a810f1) {#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1ac7323854d2947ea1866aa982c6a810f1}

#### `typedef `[`barrier_type`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a519b8a58d634736b1cc1d4484aecdddf) {#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a519b8a58d634736b1cc1d4484aecdddf}

#### `typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a409c6fbd6804e1fe800dd4389ed2a033) {#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a409c6fbd6804e1fe800dd4389ed2a033}

#### `typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a7ad6f50255ec720ea57b2ecc875104c0) {#structexot_1_1utilities_1_1workers_1_1BarrierWorker_1a7ad6f50255ec720ea57b2ecc875104c0}

# struct `exot::utilities::workers::PinnedBarrierWorker` {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker}

Synchronised worker with barriers.

The work function is performed between two barriers.

#### Parameters
* `Work` A callable object of signature void()

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`PinnedBarrierWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a641fce6c0a87ba10236bc19d64fb0728)`() = delete` | 
`public inline  `[`PinnedBarrierWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a16866a165a171e49a8ddb5eb27078cec)`(state_pointer state,unsigned int pin,`[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` policy,unsigned int priority,`[`barrier_type`](#classexot_1_1utilities_1_1Barrier)` & barrier,work_type && work,logger_pointer logger)` | Constructor for the pinned barrier worker.
`public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a3bc3289b5bfac4739808c2759c3fde1a)`()` | Main operation.
`typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a7287c7f7d0b5edfe1841e11fefc535ad) | 
`typedef `[`barrier_type`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1ac15e8128215c7332a532015ee399ae9c) | 
`typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1aba823ccbac88899d95f9728e8335f911) | 
`typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a95e79ff6e88ce5116f0c9ef7978d59d3) | 

## Members

#### `public  `[`PinnedBarrierWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a641fce6c0a87ba10236bc19d64fb0728)`() = delete` {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a641fce6c0a87ba10236bc19d64fb0728}

#### `public inline  `[`PinnedBarrierWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a16866a165a171e49a8ddb5eb27078cec)`(state_pointer state,unsigned int pin,`[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` policy,unsigned int priority,`[`barrier_type`](#classexot_1_1utilities_1_1Barrier)` & barrier,work_type && work,logger_pointer logger)` {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a16866a165a171e49a8ddb5eb27078cec}

Constructor for the pinned barrier worker.

#### Parameters
* `state` The pointer to a state object 

* `pin` The core to which the function is to be pinned 

* `policy` The scheduling policy of the executing thread 

* `priority` The scheduling priority of the executing thread 

* `work` A callable object 

* `logger` A pointer to a debug logger

#### `public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a3bc3289b5bfac4739808c2759c3fde1a)`()` {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a3bc3289b5bfac4739808c2759c3fde1a}

Main operation.

#### Parameters
* `barrier` A reference to a barrier

#### `typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a7287c7f7d0b5edfe1841e11fefc535ad) {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a7287c7f7d0b5edfe1841e11fefc535ad}

#### `typedef `[`barrier_type`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1ac15e8128215c7332a532015ee399ae9c) {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1ac15e8128215c7332a532015ee399ae9c}

#### `typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1aba823ccbac88899d95f9728e8335f911) {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1aba823ccbac88899d95f9728e8335f911}

#### `typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a95e79ff6e88ce5116f0c9ef7978d59d3) {#structexot_1_1utilities_1_1workers_1_1PinnedBarrierWorker_1a95e79ff6e88ce5116f0c9ef7978d59d3}

# struct `exot::utilities::workers::PinnedWorker` {#structexot_1_1utilities_1_1workers_1_1PinnedWorker}

[Worker](#structexot_1_1utilities_1_1workers_1_1Worker) with custom thread properties.

#### Parameters
* `Work` A callable object of signature void()

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`PinnedWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a3d39ec3a6c6e67f8479720f294157961)`() = delete` | No default constructor
`public inline  `[`PinnedWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1aa660ecea4fa97d62d02d7dfeaccc1c53)`(state_pointer state,unsigned int pin,`[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` policy,unsigned int priority,work_type && work,logger_pointer logger)` | Constructor for the pinned worker.
`public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a025f49173a878612fedbb17c7618fb7f)`()` | Main operation.
`typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a30d025eb9965336cfb443ae0ad3d1b1a) | 
`typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a64b545848a731638809177b71a65dda1) | 
`typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1aee57a4dc5542624ed6804864f162eea3) | 

## Members

#### `public  `[`PinnedWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a3d39ec3a6c6e67f8479720f294157961)`() = delete` {#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a3d39ec3a6c6e67f8479720f294157961}

No default constructor

#### `public inline  `[`PinnedWorker`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1aa660ecea4fa97d62d02d7dfeaccc1c53)`(state_pointer state,unsigned int pin,`[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` policy,unsigned int priority,work_type && work,logger_pointer logger)` {#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1aa660ecea4fa97d62d02d7dfeaccc1c53}

Constructor for the pinned worker.

#### Parameters
* `state` The pointer to a state object 

* `pin` The core to which the function is to be pinned 

* `policy` The scheduling policy of the executing thread 

* `priority` The scheduling priority of the executing thread 

* `work` A callable object 

* `logger` A pointer to a debug logger

#### `public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a025f49173a878612fedbb17c7618fb7f)`()` {#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a025f49173a878612fedbb17c7618fb7f}

Main operation.

#### `typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a30d025eb9965336cfb443ae0ad3d1b1a) {#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a30d025eb9965336cfb443ae0ad3d1b1a}

#### `typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a64b545848a731638809177b71a65dda1) {#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1a64b545848a731638809177b71a65dda1}

#### `typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1aee57a4dc5542624ed6804864f162eea3) {#structexot_1_1utilities_1_1workers_1_1PinnedWorker_1aee57a4dc5542624ed6804864f162eea3}

# struct `exot::utilities::workers::Worker` {#structexot_1_1utilities_1_1workers_1_1Worker}

Basic worker.

#### Parameters
* `Work` A callable type 

* `Args` Argument types to the callable object

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`Worker`](#structexot_1_1utilities_1_1workers_1_1Worker_1a7fcc0a000b8f14a4b3c10ec1b95d8e28)`() = delete` | No default constructor
`public inline  `[`Worker`](#structexot_1_1utilities_1_1workers_1_1Worker_1a9aafa6503d6a9f0c50a47356396f42d4)`(state_pointer state,work_type && work,logger_pointer logger)` | Constructor for the basic worker.
`public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1Worker_1a60127530ac70b1e55d268884119ac828)`(Args &&... args)` | Main operation.
`typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1Worker_1abd8bfa3b1905b4670723c5473050163d) | 
`typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1Worker_1aac320552dc0d5d28a3f0898de3701c47) | 
`typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1Worker_1a14489079a5cadecbe99b967dcc94df8f) | 

## Members

#### `public  `[`Worker`](#structexot_1_1utilities_1_1workers_1_1Worker_1a7fcc0a000b8f14a4b3c10ec1b95d8e28)`() = delete` {#structexot_1_1utilities_1_1workers_1_1Worker_1a7fcc0a000b8f14a4b3c10ec1b95d8e28}

No default constructor

#### `public inline  `[`Worker`](#structexot_1_1utilities_1_1workers_1_1Worker_1a9aafa6503d6a9f0c50a47356396f42d4)`(state_pointer state,work_type && work,logger_pointer logger)` {#structexot_1_1utilities_1_1workers_1_1Worker_1a9aafa6503d6a9f0c50a47356396f42d4}

Constructor for the basic worker.

#### Parameters
* `state` The pointer to a state object 

* `work` A callable object 

* `logger` A pointer to a debug logger

#### `public inline void `[`operator()`](#structexot_1_1utilities_1_1workers_1_1Worker_1a60127530ac70b1e55d268884119ac828)`(Args &&... args)` {#structexot_1_1utilities_1_1workers_1_1Worker_1a60127530ac70b1e55d268884119ac828}

Main operation.

#### Parameters
* `args` Arguments to the callable object `work_`

#### `typedef `[`state_pointer`](#structexot_1_1utilities_1_1workers_1_1Worker_1abd8bfa3b1905b4670723c5473050163d) {#structexot_1_1utilities_1_1workers_1_1Worker_1abd8bfa3b1905b4670723c5473050163d}

#### `typedef `[`logger_pointer`](#structexot_1_1utilities_1_1workers_1_1Worker_1aac320552dc0d5d28a3f0898de3701c47) {#structexot_1_1utilities_1_1workers_1_1Worker_1aac320552dc0d5d28a3f0898de3701c47}

#### `typedef `[`work_type`](#structexot_1_1utilities_1_1workers_1_1Worker_1a14489079a5cadecbe99b967dcc94df8f) {#structexot_1_1utilities_1_1workers_1_1Worker_1a14489079a5cadecbe99b967dcc94df8f}

# namespace `exot::utilities::workers::policy_classes::synchronisation` {#namespaceexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation}

Mixin classes that provide a function `run()`, which executes a non-returning function with the desired synchronisation method.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[`exot::utilities::workers::policy_classes::synchronisation::BarrierSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation) | Executes a function between two calls to thread barriers.
`struct `[`exot::utilities::workers::policy_classes::synchronisation::NoSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation) | Executes a function without any synchronisation.

# struct `exot::utilities::workers::policy_classes::synchronisation::BarrierSynchronisation` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation}

Executes a function between two calls to thread barriers.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a3ed0992e27b93c16d5bea1be1df9858b) | 
`public inline  `[`BarrierSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1aa5c3927490a70c3e96618d4d8cf8ffe6)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration)` & conf)` | 
`public virtual  `[`~BarrierSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a3c23f4b054eb8e821018fe736d86820a)`() = default` | 
`public inline void `[`run`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a6ea5ef4f080b2c1583c137dea14f17e7)`(std::function< void()> && f)` | 

## Members

#### `public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a3ed0992e27b93c16d5bea1be1df9858b) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a3ed0992e27b93c16d5bea1be1df9858b}

#### `public inline  `[`BarrierSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1aa5c3927490a70c3e96618d4d8cf8ffe6)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration)` & conf)` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1aa5c3927490a70c3e96618d4d8cf8ffe6}

#### `public virtual  `[`~BarrierSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a3c23f4b054eb8e821018fe736d86820a)`() = default` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a3c23f4b054eb8e821018fe736d86820a}

#### `public inline void `[`run`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a6ea5ef4f080b2c1583c137dea14f17e7)`(std::function< void()> && f)` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1a6ea5ef4f080b2c1583c137dea14f17e7}

# struct `exot::utilities::workers::policy_classes::synchronisation::NoSynchronisation` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation}

Executes a function without any synchronisation.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1ae469c642f76cc931566bcaf2246b4568) | 
`public inline  `[`NoSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1ab558e2ba8ba6fd1156df493bb6f7c673)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1_1Configuration)` & conf)` | 
`public virtual  `[`~NoSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1af6b4bbada807d173d7c8f4fff1e5a6eb)`() = default` | 
`public inline void `[`run`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1a6b5468b646c9f9f7459ce20de2b1f5e7)`(std::function< void()> && f)` | 

## Members

#### `public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1ae469c642f76cc931566bcaf2246b4568) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1ae469c642f76cc931566bcaf2246b4568}

#### `public inline  `[`NoSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1ab558e2ba8ba6fd1156df493bb6f7c673)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1_1Configuration)` & conf)` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1ab558e2ba8ba6fd1156df493bb6f7c673}

#### `public virtual  `[`~NoSynchronisation`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1af6b4bbada807d173d7c8f4fff1e5a6eb)`() = default` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1af6b4bbada807d173d7c8f4fff1e5a6eb}

#### `public inline void `[`run`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1a6b5468b646c9f9f7459ce20de2b1f5e7)`(std::function< void()> && f)` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1a6b5468b646c9f9f7459ce20de2b1f5e7}

# namespace `exot::utilities::workers::policy_classes::threading` {#namespaceexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading}

Mixin classes that allow setting thread parameters prior inside the used thread. They provide an `enforce()` function, which sets thread affinity and/or scheduling.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[`exot::utilities::workers::policy_classes::threading::BasicThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads) | 
`struct `[`exot::utilities::workers::policy_classes::threading::PinnedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads) | Workers with pinned threads and scheduling policies.
`struct `[`exot::utilities::workers::policy_classes::threading::SpecialisedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads) | Workers with pinned/un-pinned threads and scheduling policies.

# struct `exot::utilities::workers::policy_classes::threading::BasicThreads` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1aaf5816b65efe2d92037d22d3dca11cd3) | 
`public inline  `[`BasicThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a1a283ce0c4a827a4ca512253de97b0cf)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1_1Configuration)` & conf)` | 
`public virtual  `[`~BasicThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a282f15c3a1a0c7720babb02f32a90597)`() = default` | 
`public inline void `[`enforce`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a09a0de018af5f0efca3bfa799bb4c4fc)`()` | 

## Members

#### `public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1aaf5816b65efe2d92037d22d3dca11cd3) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1aaf5816b65efe2d92037d22d3dca11cd3}

#### `public inline  `[`BasicThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a1a283ce0c4a827a4ca512253de97b0cf)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1_1Configuration)` & conf)` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a1a283ce0c4a827a4ca512253de97b0cf}

#### `public virtual  `[`~BasicThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a282f15c3a1a0c7720babb02f32a90597)`() = default` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a282f15c3a1a0c7720babb02f32a90597}

#### `public inline void `[`enforce`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a09a0de018af5f0efca3bfa799bb4c4fc)`()` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1a09a0de018af5f0efca3bfa799bb4c4fc}

# struct `exot::utilities::workers::policy_classes::threading::PinnedThreads` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads}

Workers with pinned threads and scheduling policies.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1a6eba0b04cf8d1b2d2741f94810a50fb0) | 
`public inline  `[`PinnedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1ab52f69e3e68ee2baebcb8e8bed1ba86d)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration)` & conf)` | 
`public virtual  `[`~PinnedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1adf62201ed83fac04b05177bb5a118e74)`() = default` | 
`public inline void `[`enforce`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1a41c36034dd6a4977b6c40614f65f2262)`()` | 

## Members

#### `public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1a6eba0b04cf8d1b2d2741f94810a50fb0) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1a6eba0b04cf8d1b2d2741f94810a50fb0}

#### `public inline  `[`PinnedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1ab52f69e3e68ee2baebcb8e8bed1ba86d)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration)` & conf)` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1ab52f69e3e68ee2baebcb8e8bed1ba86d}

#### `public virtual  `[`~PinnedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1adf62201ed83fac04b05177bb5a118e74)`() = default` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1adf62201ed83fac04b05177bb5a118e74}

#### `public inline void `[`enforce`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1a41c36034dd6a4977b6c40614f65f2262)`()` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1a41c36034dd6a4977b6c40614f65f2262}

# struct `exot::utilities::workers::policy_classes::threading::SpecialisedThreads` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads}

Workers with pinned/un-pinned threads and scheduling policies.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a263598b391454606f0142b50b2c2d05a) | 
`public inline  `[`SpecialisedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a0a6ca9aa0ca88cfd533117432fb73953)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration)` & conf)` | 
`public virtual  `[`~SpecialisedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a5634b0adc3553e8820ea9143dc4c36d3)`() = default` | 
`public inline void `[`enforce`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a97869648e4cfef270919a4de385e1992)`()` | 

## Members

#### `public `[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration)` `[`conf_`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a263598b391454606f0142b50b2c2d05a) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a263598b391454606f0142b50b2c2d05a}

#### `public inline  `[`SpecialisedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a0a6ca9aa0ca88cfd533117432fb73953)`(`[`Configuration`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration)` & conf)` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a0a6ca9aa0ca88cfd533117432fb73953}

#### `public virtual  `[`~SpecialisedThreads`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a5634b0adc3553e8820ea9143dc4c36d3)`() = default` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a5634b0adc3553e8820ea9143dc4c36d3}

#### `public inline void `[`enforce`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a97869648e4cfef270919a4de385e1992)`()` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1a97869648e4cfef270919a4de385e1992}

# namespace `fmt` {#namespacefmt}

Overloads that target the fmtlib directly

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[`fmt::formatter< std::optional< T > >`](#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4) | Formatter for optional types.

# struct `fmt::formatter< std::optional< T > >` {#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4}

Formatter for optional types.

Uses default formatter "{}".

#### Parameters
* `T` The type encapsulated by std::optional

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public template<>`  <br/>`inline constexpr auto `[`parse`](#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4_1a23458d304e7b597a336dc5f17265f656)`(ParseContext & ctx)` | 
`public template<>`  <br/>`inline auto `[`format`](#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4_1afb5d19c8e2e134788b373d64e7c5be38)`(const std::optional< T > & p,FormatContext & ctx)` | 

## Members

#### `public template<>`  <br/>`inline constexpr auto `[`parse`](#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4_1a23458d304e7b597a336dc5f17265f656)`(ParseContext & ctx)` {#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4_1a23458d304e7b597a336dc5f17265f656}

#### `public template<>`  <br/>`inline auto `[`format`](#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4_1afb5d19c8e2e134788b373d64e7c5be38)`(const std::optional< T > & p,FormatContext & ctx)` {#structfmt_1_1formatter_3_01std_1_1optional_3_01T_01_4_01_4_1afb5d19c8e2e134788b373d64e7c5be38}

# namespace `nlohmann` {#namespacenlohmann}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`struct `[`nlohmann::adl_serializer< exot::utilities::SchedulingPolicy >`](#structnlohmann_1_1adl__serializer_3_01exot_1_1utilities_1_1SchedulingPolicy_01_4) | Overload of the json serialiser for SchedulingPolicy.
`struct `[`nlohmann::adl_serializer< spdlog::level::level_enum >`](#structnlohmann_1_1adl__serializer_3_01spdlog_1_1level_1_1level__enum_01_4) | Overload of the json serialiser for SPDLOG's log level.
`struct `[`nlohmann::adl_serializer< std::chrono::duration< Rep, Period > >`](#structnlohmann_1_1adl__serializer_3_01std_1_1chrono_1_1duration_3_01Rep_00_01Period_01_4_01_4) | Overload of the json serialiser for std::chrono::duration.
`struct `[`nlohmann::adl_serializer< std::optional< T > >`](#structnlohmann_1_1adl__serializer_3_01std_1_1optional_3_01T_01_4_01_4) | Overload of the json serialiser for std::optional wrapped types.

# struct `nlohmann::adl_serializer< exot::utilities::SchedulingPolicy >` {#structnlohmann_1_1adl__serializer_3_01exot_1_1utilities_1_1SchedulingPolicy_01_4}

Overload of the json serialiser for SchedulingPolicy.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `nlohmann::adl_serializer< spdlog::level::level_enum >` {#structnlohmann_1_1adl__serializer_3_01spdlog_1_1level_1_1level__enum_01_4}

Overload of the json serialiser for SPDLOG's log level.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `nlohmann::adl_serializer< std::chrono::duration< Rep, Period > >` {#structnlohmann_1_1adl__serializer_3_01std_1_1chrono_1_1duration_3_01Rep_00_01Period_01_4_01_4}

Overload of the json serialiser for std::chrono::duration.

Values are written to and from numeric values in seconds. For example, to write a nanosecond to a duration object, write 1e-9 in the JSON file. The target type might not be able to hold the specified duration!

#### Parameters
* `Rep` Underlying type representing the duration object. 

* `Period` A std::ratio representing the tick period.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `nlohmann::adl_serializer< std::optional< T > >` {#structnlohmann_1_1adl__serializer_3_01std_1_1optional_3_01T_01_4_01_4}

Overload of the json serialiser for std::optional wrapped types.

#### Parameters
* `T` The type "carried" by std::optional

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `std` {#namespacestd}

These have to be accessible from the global namespace

These have to be registered in the global namespace in order to benefit from fmtlib's ostream formatting.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public template<>`  <br/>`std::basic_istream< CharT, CharTraitsT > & `[`operator>>`](#namespacestd_1afa031dfe64926c70f7fb8bdfe8f5c637)`(std::basic_istream< CharT, CharTraitsT > & stream,std::tuple< Ts... > & tuple)`            | Input stream operator overload for reading tuples.
`public template<>`  <br/>`std::enable_if<(`[`exot::utilities::is_iterable](#structexot_1_1utilities_1_1is__iterable)< T >::value &&[exot::utilities::has_push_back`](#structexot_1_1utilities_1_1has__push__back)< T >::value)`, std::basic_istream< CharT, CharTraitsT > & >::type & `[`operator>>`](#namespacestd_1a461709d03777b3b4cb77bfbaaaf16cc6)`(std::basic_istream< CharT, CharTraitsT > & istream,T & container)`            | Input stream operator overload for reading into appendable containers. The container has to have a `push_back()` function.
`public template<>`  <br/>`std::basic_istream< CharT, CharTraitsT > & `[`operator>>`](#namespacestd_1aa14cdd42cbf3c4a16109a77aea298ff6)`(std::basic_istream< CharT, CharTraitsT > & istream,std::array< T, N > & container)`            | Input stream operator overload for reading into fixed-size arrays.
`public template<>`  <br/>`std::enable_if< `[`exot::utilities::is_iterable](#structexot_1_1utilities_1_1is__iterable)< T >::value &&![exot::utilities::is_const_iterable`](#structexot_1_1utilities_1_1is__const__iterable)`< T >::value, std::basic_ostream< CharT, CharTraitsT > & >::type & `[`operator<<`](#namespacestd_1a5ff199ec3414ff4cb06e0a2d234ab3c0)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const T & range)`            | Outputs iterable types to std::basic_ostream.
`public template<>`  <br/>`std::enable_if< `[`exot::utilities::is_const_iterable`](#structexot_1_1utilities_1_1is__const__iterable)`< T >::value, std::basic_ostream< CharT, CharTraitsT > & >::type & `[`operator<<`](#namespacestd_1a1c0aac5949fa0149619c8733e5ae6b01)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const T & range)`            | Outputs const iterable types to std::basic_ostream.
`public template<>`  <br/>`std::enable_if< `[`exot::utilities::is_tuple`](#structexot_1_1utilities_1_1is__tuple)`< T >::value, std::basic_ostream< CharT, CharTraitsT > >::type & `[`operator<<`](#namespacestd_1a1d384a85045615670dc96b7cd95f84f0)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const T & tuple)`            | Outputs tuples to std::basic_ostream.
`public template<>`  <br/>`std::basic_ostream< CharT, CharTraitsT > & `[`operator<<`](#namespacestd_1a2832ca2a06c8c68ed141da8381bc606e)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const std::chrono::duration< Rep, Period > & duration)`            | Outputs durations to std::basic_ostream.

## Members

#### `public template<>`  <br/>`std::basic_istream< CharT, CharTraitsT > & `[`operator>>`](#namespacestd_1afa031dfe64926c70f7fb8bdfe8f5c637)`(std::basic_istream< CharT, CharTraitsT > & stream,std::tuple< Ts... > & tuple)` {#namespacestd_1afa031dfe64926c70f7fb8bdfe8f5c637}

Input stream operator overload for reading tuples.

> Todo: The function may not work when the tuple holds iterable types

#### Parameters
* `stream` The stream 

* `tuple` The tuple

#### Parameters
* `CharT` Character type used by the stream 

* `CharTraitsT` Character traits used by the stream 

* `Ts` Types held by the tuple

#### Returns
The stream

#### `public template<>`  <br/>`std::enable_if<(`[`exot::utilities::is_iterable](#structexot_1_1utilities_1_1is__iterable)< T >::value &&[exot::utilities::has_push_back`](#structexot_1_1utilities_1_1has__push__back)< T >::value)`, std::basic_istream< CharT, CharTraitsT > & >::type & `[`operator>>`](#namespacestd_1a461709d03777b3b4cb77bfbaaaf16cc6)`(std::basic_istream< CharT, CharTraitsT > & istream,T & container)` {#namespacestd_1a461709d03777b3b4cb77bfbaaaf16cc6}

Input stream operator overload for reading into appendable containers. The container has to have a `push_back()` function.

#### Parameters
* `istream` The input stream 

* `container` The container

#### Parameters
* `T` The type of the container 

* `CharT` Character type used by the stream 

* `CharTraitsT` Character traits used by the stream

#### Returns
The stream

#### `public template<>`  <br/>`std::basic_istream< CharT, CharTraitsT > & `[`operator>>`](#namespacestd_1aa14cdd42cbf3c4a16109a77aea298ff6)`(std::basic_istream< CharT, CharTraitsT > & istream,std::array< T, N > & container)` {#namespacestd_1aa14cdd42cbf3c4a16109a77aea298ff6}

Input stream operator overload for reading into fixed-size arrays.

#### Parameters
* `istream` The input stream 

* `container` The array

#### Parameters
* `T` The value type stored in the array 

* `N` The size of the array 

* `CharT` Character type used by the stream 

* `CharTraitsT` Character traits used by the stream

#### Returns
The stream

#### `public template<>`  <br/>`std::enable_if< `[`exot::utilities::is_iterable](#structexot_1_1utilities_1_1is__iterable)< T >::value &&![exot::utilities::is_const_iterable`](#structexot_1_1utilities_1_1is__const__iterable)`< T >::value, std::basic_ostream< CharT, CharTraitsT > & >::type & `[`operator<<`](#namespacestd_1a5ff199ec3414ff4cb06e0a2d234ab3c0)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const T & range)` {#namespacestd_1a5ff199ec3414ff4cb06e0a2d234ab3c0}

Outputs iterable types to std::basic_ostream.

#### Parameters
* `ostream` The output stream 

* `range` The iterable range

#### Parameters
* `T` Type of the iterable range 

* `CharT` Character type used by basic_ostream 

* `CharTraitsT` Character traits used by basic_ostream

#### Returns
The output stream

#### `public template<>`  <br/>`std::enable_if< `[`exot::utilities::is_const_iterable`](#structexot_1_1utilities_1_1is__const__iterable)`< T >::value, std::basic_ostream< CharT, CharTraitsT > & >::type & `[`operator<<`](#namespacestd_1a1c0aac5949fa0149619c8733e5ae6b01)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const T & range)` {#namespacestd_1a1c0aac5949fa0149619c8733e5ae6b01}

Outputs const iterable types to std::basic_ostream.

If the range type is const iterable, prefer this overload.

#### Parameters
* `ostream` The output stream 

* `range` The const iterable range

#### Parameters
* `T` Type of the const iterable range 

* `CharT` Character type used by basic_ostream 

* `CharTraitsT` Character traits used by basic_ostream

#### Returns
The output stream

#### `public template<>`  <br/>`std::enable_if< `[`exot::utilities::is_tuple`](#structexot_1_1utilities_1_1is__tuple)`< T >::value, std::basic_ostream< CharT, CharTraitsT > >::type & `[`operator<<`](#namespacestd_1a1d384a85045615670dc96b7cd95f84f0)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const T & tuple)` {#namespacestd_1a1d384a85045615670dc96b7cd95f84f0}

Outputs tuples to std::basic_ostream.

Uses a compile time for loop to iterate over tuple elements.

#### Parameters
* `ostream` The output stream 

* `tuple` The tuple

#### Parameters
* `T` Type of the tuple 

* `CharT` Character type used by basic_ostream 

* `CharTraitsT` Character traits used by basic_ostream

#### Returns
The output stream

#### `public template<>`  <br/>`std::basic_ostream< CharT, CharTraitsT > & `[`operator<<`](#namespacestd_1a2832ca2a06c8c68ed141da8381bc606e)`(std::basic_ostream< CharT, CharTraitsT > & ostream,const std::chrono::duration< Rep, Period > & duration)` {#namespacestd_1a2832ca2a06c8c68ed141da8381bc606e}

Outputs durations to std::basic_ostream.

Simply calls the `count()` method of the duration object.

#### Parameters
* `ostream` The output stream 

* `duration` The chrono duration object

#### Parameters
* `CharT` Character type used by basic_ostream 

* `CharTraitsT` Character traits used by basic_ostream 

* `Rep` Underlying type used in the chrono duration 

* `Period` Ratio used in the chrono duration (e.g. ns)

#### Returns
The output stream

# struct `exot::utilities::workers::policy_classes::synchronisation::BarrierSynchronisation::Configuration` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public `[`exot::utilities::Barrier`](#classexot_1_1utilities_1_1Barrier)` & `[`barrier`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration_1a3f41d0a7d5faaad2171211736e31071d) | 

## Members

#### `public `[`exot::utilities::Barrier`](#classexot_1_1utilities_1_1Barrier)` & `[`barrier`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration_1a3f41d0a7d5faaad2171211736e31071d) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1BarrierSynchronisation_1_1Configuration_1a3f41d0a7d5faaad2171211736e31071d}

# struct `exot::utilities::workers::policy_classes::synchronisation::NoSynchronisation::Configuration` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1synchronisation_1_1NoSynchronisation_1_1Configuration}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::workers::policy_classes::threading::BasicThreads::Configuration` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1BasicThreads_1_1Configuration}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::utilities::workers::policy_classes::threading::PinnedThreads::Configuration` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public const unsigned int `[`pin`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1aef77a12e8f278b2328a7e23413cc00e9) | 
`public const `[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` `[`policy`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1a60bb02725a12796e6a89844f3646c2ac) | Core to pin.
`public const unsigned int `[`priority`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1a138f94c8d9214b20e9acb524b4ec2c73) | Scheduling policy.

## Members

#### `public const unsigned int `[`pin`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1aef77a12e8f278b2328a7e23413cc00e9) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1aef77a12e8f278b2328a7e23413cc00e9}

#### `public const `[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` `[`policy`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1a60bb02725a12796e6a89844f3646c2ac) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1a60bb02725a12796e6a89844f3646c2ac}

Core to pin.

#### `public const unsigned int `[`priority`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1a138f94c8d9214b20e9acb524b4ec2c73) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1PinnedThreads_1_1Configuration_1a138f94c8d9214b20e9acb524b4ec2c73}

Scheduling policy.

# struct `exot::utilities::workers::policy_classes::threading::SpecialisedThreads::Configuration` {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public const unsigned int `[`pin`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a29641365531fad81e2dc44ca3242cbf1) | 
`public const bool `[`should_pin`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a0b075573f40aee87102b91b9dbcf4644) | Core to pin.
`public const `[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` `[`policy`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a8c11e4d71025ccd198a1534bde9e9ebe) | Should pin?
`public const unsigned int `[`priority`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a5f740585b1ab5a30ca1b94c7999007bc) | Scheduling policy.

## Members

#### `public const unsigned int `[`pin`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a29641365531fad81e2dc44ca3242cbf1) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a29641365531fad81e2dc44ca3242cbf1}

#### `public const bool `[`should_pin`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a0b075573f40aee87102b91b9dbcf4644) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a0b075573f40aee87102b91b9dbcf4644}

Core to pin.

#### `public const `[`exot::utilities::SchedulingPolicy`](#namespaceexot_1_1utilities_1a63dddf474cd6bf104d3641c343102dd7)` `[`policy`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a8c11e4d71025ccd198a1534bde9e9ebe) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a8c11e4d71025ccd198a1534bde9e9ebe}

Should pin?

#### `public const unsigned int `[`priority`](#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a5f740585b1ab5a30ca1b94c7999007bc) {#structexot_1_1utilities_1_1workers_1_1policy__classes_1_1threading_1_1SpecialisedThreads_1_1Configuration_1a5f740585b1ab5a30ca1b94c7999007bc}

Scheduling policy.

# struct `exot::utilities::AlignedAllocator::rebind` {#structexot_1_1utilities_1_1AlignedAllocator_1_1rebind}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`other`](#structexot_1_1utilities_1_1AlignedAllocator_1_1rebind_1abe609be2152798ebf95776d000d731e9) | 

## Members

#### `typedef `[`other`](#structexot_1_1utilities_1_1AlignedAllocator_1_1rebind_1abe609be2152798ebf95776d000d731e9) {#structexot_1_1utilities_1_1AlignedAllocator_1_1rebind_1abe609be2152798ebf95776d000d731e9}

# struct `exot::utilities::Logging::settings` {#structexot_1_1utilities_1_1Logging_1_1settings}

```
struct exot::utilities::Logging::settings
  : public exot::utilities::configurable< settings >
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public std::optional< std::string > `[`debug_log_filename`](#structexot_1_1utilities_1_1Logging_1_1settings_1ae766d252cc51cb351d70b9cf515266cd) | 
`public std::optional< std::string > `[`app_log_filename`](#structexot_1_1utilities_1_1Logging_1_1settings_1a646c8d23e8d5a98ddaf20dcf3ce328d4) | 
`public spdlog::level::level_enum `[`log_level`](#structexot_1_1utilities_1_1Logging_1_1settings_1a38581c923728e4c614da172bc67cddb3) | 
`public size_t `[`async_size`](#structexot_1_1utilities_1_1Logging_1_1settings_1ad579494e0304e07d2ec609af38d2eccf) | 
`public bool `[`async`](#structexot_1_1utilities_1_1Logging_1_1settings_1aebda9b9ee58bf91f25f34ec6d8aa3344) | 
`public size_t `[`async_thread_count`](#structexot_1_1utilities_1_1Logging_1_1settings_1a7cccc9ce741025c3942d9bb427ed3bc5) | 
`public bool `[`timestamp_files`](#structexot_1_1utilities_1_1Logging_1_1settings_1a3157a51c4f4d74d801a254e024c4484c) | 
`public bool `[`rotating_logs`](#structexot_1_1utilities_1_1Logging_1_1settings_1a36cda50d0094f9f9c999691bcbf01865) | 
`public bool `[`provide_platform_identification`](#structexot_1_1utilities_1_1Logging_1_1settings_1ab5e95ce1430a3099020b8e685bda9e33) | 
`public bool `[`append_governor_to_files`](#structexot_1_1utilities_1_1Logging_1_1settings_1aff6ca42a7f0141a2754fbd6b77dc7a6a) | 
`public size_t `[`rotating_logs_size`](#structexot_1_1utilities_1_1Logging_1_1settings_1a1c7e4f53a6b4b140d5b134edd7d498cc) | 
`public size_t `[`rotating_logs_count`](#structexot_1_1utilities_1_1Logging_1_1settings_1a659a1b85b12a3b286213329c86555cb6) | 
`public inline const char * `[`name`](#structexot_1_1utilities_1_1Logging_1_1settings_1aeef29ee02cd60ff6f5dbbd86d94120bc)`() const` | 
`public inline void `[`configure`](#structexot_1_1utilities_1_1Logging_1_1settings_1acd679cec46ac4d63f66e77dc90a96621)`()` | 

## Members

#### `public std::optional< std::string > `[`debug_log_filename`](#structexot_1_1utilities_1_1Logging_1_1settings_1ae766d252cc51cb351d70b9cf515266cd) {#structexot_1_1utilities_1_1Logging_1_1settings_1ae766d252cc51cb351d70b9cf515266cd}

#### `public std::optional< std::string > `[`app_log_filename`](#structexot_1_1utilities_1_1Logging_1_1settings_1a646c8d23e8d5a98ddaf20dcf3ce328d4) {#structexot_1_1utilities_1_1Logging_1_1settings_1a646c8d23e8d5a98ddaf20dcf3ce328d4}

#### `public spdlog::level::level_enum `[`log_level`](#structexot_1_1utilities_1_1Logging_1_1settings_1a38581c923728e4c614da172bc67cddb3) {#structexot_1_1utilities_1_1Logging_1_1settings_1a38581c923728e4c614da172bc67cddb3}

#### `public size_t `[`async_size`](#structexot_1_1utilities_1_1Logging_1_1settings_1ad579494e0304e07d2ec609af38d2eccf) {#structexot_1_1utilities_1_1Logging_1_1settings_1ad579494e0304e07d2ec609af38d2eccf}

#### `public bool `[`async`](#structexot_1_1utilities_1_1Logging_1_1settings_1aebda9b9ee58bf91f25f34ec6d8aa3344) {#structexot_1_1utilities_1_1Logging_1_1settings_1aebda9b9ee58bf91f25f34ec6d8aa3344}

#### `public size_t `[`async_thread_count`](#structexot_1_1utilities_1_1Logging_1_1settings_1a7cccc9ce741025c3942d9bb427ed3bc5) {#structexot_1_1utilities_1_1Logging_1_1settings_1a7cccc9ce741025c3942d9bb427ed3bc5}

#### `public bool `[`timestamp_files`](#structexot_1_1utilities_1_1Logging_1_1settings_1a3157a51c4f4d74d801a254e024c4484c) {#structexot_1_1utilities_1_1Logging_1_1settings_1a3157a51c4f4d74d801a254e024c4484c}

#### `public bool `[`rotating_logs`](#structexot_1_1utilities_1_1Logging_1_1settings_1a36cda50d0094f9f9c999691bcbf01865) {#structexot_1_1utilities_1_1Logging_1_1settings_1a36cda50d0094f9f9c999691bcbf01865}

#### `public bool `[`provide_platform_identification`](#structexot_1_1utilities_1_1Logging_1_1settings_1ab5e95ce1430a3099020b8e685bda9e33) {#structexot_1_1utilities_1_1Logging_1_1settings_1ab5e95ce1430a3099020b8e685bda9e33}

#### `public bool `[`append_governor_to_files`](#structexot_1_1utilities_1_1Logging_1_1settings_1aff6ca42a7f0141a2754fbd6b77dc7a6a) {#structexot_1_1utilities_1_1Logging_1_1settings_1aff6ca42a7f0141a2754fbd6b77dc7a6a}

#### `public size_t `[`rotating_logs_size`](#structexot_1_1utilities_1_1Logging_1_1settings_1a1c7e4f53a6b4b140d5b134edd7d498cc) {#structexot_1_1utilities_1_1Logging_1_1settings_1a1c7e4f53a6b4b140d5b134edd7d498cc}

#### `public size_t `[`rotating_logs_count`](#structexot_1_1utilities_1_1Logging_1_1settings_1a659a1b85b12a3b286213329c86555cb6) {#structexot_1_1utilities_1_1Logging_1_1settings_1a659a1b85b12a3b286213329c86555cb6}

#### `public inline const char * `[`name`](#structexot_1_1utilities_1_1Logging_1_1settings_1aeef29ee02cd60ff6f5dbbd86d94120bc)`() const` {#structexot_1_1utilities_1_1Logging_1_1settings_1aeef29ee02cd60ff6f5dbbd86d94120bc}

#### `public inline void `[`configure`](#structexot_1_1utilities_1_1Logging_1_1settings_1acd679cec46ac4d63f66e77dc90a96621)`()` {#structexot_1_1utilities_1_1Logging_1_1settings_1acd679cec46ac4d63f66e77dc90a96621}

Generated by [Moxygen](https://sourcey.com/moxygen)
