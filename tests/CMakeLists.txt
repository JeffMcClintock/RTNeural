include_directories(../RTNeural)

add_executable(rtneural_tests tests.cpp)
target_link_libraries(rtneural_tests LINK_PUBLIC RTNeural)
target_compile_definitions(rtneural_tests PRIVATE RTNEURAL_ROOT_DIR="${CMAKE_SOURCE_DIR}/")

add_test(NAME "RTNeural_Bad_Model_Test" COMMAND $<TARGET_FILE:rtneural_tests> bad_model)
add_test(NAME "RTNeural_Model_Test" COMMAND $<TARGET_FILE:rtneural_tests> model)
add_test(NAME "RTNeural_Sample_Rate_RNN_Test" COMMAND $<TARGET_FILE:rtneural_tests> sample_rate_rnn)
add_test(NAME "RTNeural_Torch_Test" COMMAND $<TARGET_FILE:rtneural_tests> torch)
add_test(NAME "RTNeural_Util_Test" COMMAND $<TARGET_FILE:rtneural_tests> util)
add_test(NAME "RTNeural_Conv1D_Test" COMMAND $<TARGET_FILE:rtneural_tests> conv1d)
add_test(NAME "RTNeural_Conv2D_Test" COMMAND $<TARGET_FILE:rtneural_tests> conv2d)
add_test(NAME "RTNeural_Dense_Test" COMMAND $<TARGET_FILE:rtneural_tests> dense)
add_test(NAME "RTNeural_GRU_Test" COMMAND $<TARGET_FILE:rtneural_tests> gru)
add_test(NAME "RTNeural_GRU_1D_Test" COMMAND $<TARGET_FILE:rtneural_tests> gru_1d)
add_test(NAME "RTNeural_LSTM_Test" COMMAND $<TARGET_FILE:rtneural_tests> lstm)
add_test(NAME "RTNeural_LSTM_1D_Test" COMMAND $<TARGET_FILE:rtneural_tests> lstm_1d)

option(RTNEURAL_CODE_COVERAGE "Build RTNeural tests with code coverage flags" OFF)
if(RTNEURAL_CODE_COVERAGE)
    include(${CMAKE_CURRENT_SOURCE_DIR}/../cmake/EnableCoverageFlags.cmake)
    enable_coverage_flags(rtneural_tests)
endif()
