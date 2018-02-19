cmake_minimum_required(VERSION 3.7)
project(core)

set(CMAKE_CXX_STANDARD 11)

include_directories(
        src
        src/json
        src/leveldb
        src/leveldb/helpers
        src/leveldb/include
        src/leveldb/table
        src/leveldb/util
        src/zerocoin
)

add_definitions(
        -DLEVELDB_PLATFORM_POSIX
        -DTEST_DATA_DIR="${CMAKE_CURRENT_SOURCE_DIR}/src/test/data"
)

set(CMAKE_CXX_FLAGS_DEBUG "-g -O0")

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/CMakeModules")

find_package(BerkeleyDB REQUIRED)
find_package(Boost COMPONENTS program_options thread system filesystem unit_test_framework REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(Threads REQUIRED)

include_directories(
        ${BDB_INCLUDE_DIR}
        ${Boost_INCLUDE_DIRS}
        ${OPENSSL_INCLUDE_DIR}
)

add_library(core
        src/json/json_spirit_reader.cpp
        src/json/json_spirit_value.cpp
        src/json/json_spirit_writer.cpp
        src/leveldb/db/builder.cc
        src/leveldb/db/c.cc
        src/leveldb/db/db_impl.cc
        src/leveldb/db/db_iter.cc
        src/leveldb/db/dbformat.cc
        src/leveldb/db/filename.cc
        src/leveldb/db/log_reader.cc
        src/leveldb/db/log_writer.cc
        src/leveldb/db/memtable.cc
        src/leveldb/db/repair.cc
        src/leveldb/db/table_cache.cc
        src/leveldb/db/version_edit.cc
        src/leveldb/db/version_set.cc
        src/leveldb/db/write_batch.cc
        src/leveldb/helpers/memenv/memenv.cc
        src/leveldb/table/block.cc
        src/leveldb/table/block_builder.cc
        src/leveldb/table/filter_block.cc
        src/leveldb/table/format.cc
        src/leveldb/table/iterator.cc
        src/leveldb/table/merger.cc
        src/leveldb/table/table.cc
        src/leveldb/table/table_builder.cc
        src/leveldb/table/two_level_iterator.cc
        src/leveldb/util/arena.cc
        src/leveldb/util/bloom.cc
        src/leveldb/util/cache.cc
        src/leveldb/util/coding.cc
        src/leveldb/util/comparator.cc
        src/leveldb/util/crc32c.cc
        src/leveldb/util/env.cc
        src/leveldb/util/env_posix.cc
        src/leveldb/util/env_win.cc
        src/leveldb/util/filter_policy.cc
        src/leveldb/util/hash.cc
        src/leveldb/util/histogram.cc
        src/leveldb/util/logging.cc
        src/leveldb/util/options.cc
        src/leveldb/util/status.cc
        src/leveldb/port/port_posix.cc
        src/zerocoin/Accumulator.cpp
        src/zerocoin/AccumulatorProofOfKnowledge.cpp
        src/zerocoin/Coin.cpp
        src/zerocoin/CoinSpend.cpp
        src/zerocoin/Commitment.cpp
        src/zerocoin/ParamGeneration.cpp
        src/zerocoin/Params.cpp
        src/zerocoin/SerialNumberSignatureOfKnowledge.cpp
        src/zerocoin/SpendMetaData.cpp
        src/zerocoin/ZeroTest.cpp
        src/alert.cpp
        src/version.cpp
        src/checkpoints.cpp
        src/netbase.cpp
        src/addrman.cpp
        src/crypter.cpp
        src/key.cpp
        src/db.cpp
        src/irc.cpp
        src/keystore.cpp
        src/miner.cpp
        src/main.cpp
        src/net.cpp
        src/protocol.cpp
        src/bitcoinrpc.cpp
        src/rpcdump.cpp
        src/rpcnet.cpp
        src/rpcmining.cpp
        src/rpcwallet.cpp
        src/rpcblockchain.cpp
        src/rpcrawtransaction.cpp
        src/script.cpp
        src/sync.cpp
        src/util.cpp
        src/wallet.cpp
        src/walletdb.cpp
        src/noui.cpp
        src/kernel.cpp
        src/pbkdf2.cpp
        src/scrypt.cpp
        src/txdb-leveldb.cpp
        src/init.cpp
)

add_executable(test_neetcoin
        src/test/accounting_tests.cpp
        src/test/allocator_tests.cpp
        src/test/base32_tests.cpp
        src/test/base64_tests.cpp
        src/test/bignum_tests.cpp
        src/test/getarg_tests.cpp
        src/test/key_tests.cpp
        src/test/mruset_tests.cpp
        src/test/netbase_tests.cpp
        src/test/rpc_tests.cpp
        src/test/script_tests.cpp
        src/test/sigopcount_tests.cpp
        src/test/test_bitcoin.cpp
        src/test/uint160_tests.cpp
        src/test/uint256_tests.cpp
        src/test/util_tests.cpp
        src/test/wallet_tests.cpp
)

target_link_libraries(test_neetcoin
        core
        ${BDB_LIBRARIES}
        ${Boost_LIBRARIES}
        ${CMAKE_THREAD_LIBS_INIT}
        ${OPENSSL_LIBRARIES}
)
