add_executable(amg2013 amg2013.c )
target_link_libraries(amg2013 PRIVATE libHYPRE_utilities parcsr_ls parcsr_mv seq_mv sstruct_mv libIJ_mv struct_mv krylov ${MPI_LIBRARIES})
target_include_directories(amg2013 PRIVATE ../ ../utilities ../struct_mv ../sstruct_mv ../IJ_mv ../seq_mv ../parcsr_mv ../parcsr_ls ../krylov)
target_compile_options(amg2013 PRIVATE -DHYPRE_TIMING)
target_link_directories(amg2013 PRIVATE ../utilities ../struct_mv ../sstruct_mv ../IJ_mv ../seq_mv ../parcsr_mv ../parcsr_ls ../krylov)

if(MPI_COMPILE_FLAGS)
    set_target_properties(amg2013 PROPERTIES
            COMPILE_FLAGS "${MPI_COMPILE_FLAGS}")
endif()

if(MPI_LINK_FLAGS)
    set_target_properties(amg2013 PROPERTIES
            LINK_FLAGS "${MPI_LINK_FLAGS}")
endif()

configure_file(sstruct.in.MG.FD sstruct.in.MG.FD COPYONLY)