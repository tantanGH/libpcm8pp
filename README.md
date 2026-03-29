# libpcm8pp
PCM8PP - C bridge library for X68k

elf2x68k環境向けのPCM8PPドライバのファンクションコールラッパーCライブラリです。

PCM8PPのファンクションコールに準じた以下の関数が利用可能です。
```
int32_t pcm8pp_play(int16_t channel, uint32_t mode, size_t size, uint32_t freq, void* addr);
int32_t pcm8pp_play_array_chain(int16_t channel, uint32_t mode, size_t count, uint32_t freq, void* addr);
int32_t pcm8pp_play_linked_array_chain(int16_t channel, uint32_t mode, size_t size, uint32_t freq, void* addr);
int32_t pcm8pp_play_ex_linked_array_chain(int16_t channel, uint32_t mode, size_t size, uint32_t freq, void* addr);
int32_t pcm8pp_set_channel_mode(int16_t channel, uint32_t mode, uint32_t freq);
int32_t pcm8pp_get_data_length(int16_t channel);
int32_t pcm8pp_get_channel_mode(int16_t channel);
int32_t pcm8pp_get_block_counter(int16_t channel);
int32_t pcm8pp_stop();
int32_t pcm8pp_pause();
int32_t pcm8pp_resume();
int32_t pcm8pp_get_max_channels();
int32_t pcm8pp_set_max_channels(int16_t channels);
int32_t pcm8pp_set_polyphonic_mode(int16_t mode);
int32_t pcm8pp_get_frequency_mode();
int32_t pcm8pp_set_frequency_mode(int16_t mode);
```

また、PCM8PPの常駐確認およびまーきゅりーゆにっとのバージョンチェックを行う関数も利用可能です。
```
int32_t pcm8pp_isavailable();
int32_t pcm8pp_get_mercury_version();
```


使う時は、サブモジュールとして組み込むのが簡単です。例えばプロジェクト直下にて以下を実行します。

```
git submodule add https://github.com/tantanGH/libpcm8pp.git libs/libpcm8pp
```

以下のようなツリーとなります。

```
my_app/
├── .git/
├── .gitmodules
├── libs/
│   └── libpcm8pp/
│       ├── include/pcm8pp.h
│       └── lib/libpcm8pp.a
└── src/
    ├── main.c
    └── Makefile
```

ヘッダー検索パスとライブラリ検索パスをMakefile内で
```
-I../libs/libj/include
-L../libs/libj/lib
```
のように指定し、`-lpcm8pp` でリンクできます。