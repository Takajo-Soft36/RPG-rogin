
# include <Siv3D.hpp>

void Main()
{
	const Font font(20);

	while (System::Update())
	{
		Input::GetCharsHelper(text);

		font(text).draw();
	}
}
[ログイン](https://takajo-soft36.github.io/RPG-rogin/rog.md)


