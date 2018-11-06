

void Main()
{
	const Font font(20);

	// 空の String
	String text;

	while (System::Update())
	{
		// text を入力された文字列で更新する
		// バックスペースやタブ、改行も有効
		Input::GetCharsHelper(text);

		font(text).draw();
	}
}
[ログイン](https://takajo-soft36.github.io/RPG-rogin/rog.md)


