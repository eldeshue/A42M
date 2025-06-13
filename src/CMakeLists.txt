cmake_minimum_required(VERSION 3.23)

# 현재 디렉토리에 있는 모든 파일을 SRC_FILES 변수에 추가한다.
file(GLOB_RECURSE SRC_FILES CONFIGURE_DEPENDS
  ${CMAKE_CURRENT_SOURCE_DIR}/*.cc
)

add_library(a42m STATIC ${SRC_FILES})

target_include_directories(a42m
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include      # 공개 헤더 (API)
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/lib    # 내부 전용 헤더
)

# 현재 타겟에 대한 정적 링킹 추가
# lib 아래에 추가한 라이브러리를 여기에 추가
# target_link_libraries(타겟이름 PUBLIC 링크할라이브러리이름)
