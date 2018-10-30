rogin画面
# include <Siv3D.hpp>

class CharButton
{
private:

	String m_text;

	Rect m_rect;

	bool m_pressed = false;

public:

	CharButton() = default;

	CharButton(const String& text, const Rect& rect)
		: m_text(text)
		, m_rect(rect) {}

	bool update()
	{
		if (m_rect.leftClicked)
		{
			m_pressed = true;
		}
		else if (m_pressed && !m_rect.mouseOver)
		{
			m_pressed = false;
		}
		else if (m_pressed && m_rect.leftReleased)
		{
			m_pressed = false;

			return true;
		}

		return false;
	}

	void draw() const
	{
		const Color color(m_pressed ? 220 : m_rect.mouseOver ? 240 : 255);

		RoundRect(m_rect, 4).draw(color);

		FontAsset(L"Button")(m_text).drawAt(m_rect.center, Palette::Black);
	}

	const String& getText() const
	{
		return m_text;
	}

	const Rect& getRect() const
	{
		return m_rect;
	}
};

void Main()
{
	Graphics::SetBackground(Palette::Skyblue);

	FontAsset::Register(L"Name", 30);

	FontAsset::Register(L"Button", 15, Typeface::Medium);

	String name;

	const size_t maxNameLength = 18;

	const String chars = L"ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!?'-_#";

	Array<CharButton> buttons;

	for (auto i : step(chars.length))
	{
		const int32 x = (i % 12) * 50 + 23;
		const int32 y = (i / 12) * 50 + 200;
		buttons.emplace_back(String(1, chars[i]), Rect(x, y, 44, 44));
	}

	buttons.emplace_back(L" ", Rect(6 * 50 + 23, 3 * 50 + 200, 144, 44));

	buttons.emplace_back(L"[BS]", Rect(9 * 50 + 23, 3 * 50 + 200, 94, 44));

	while (System::Update())
	{
		for (auto& button : buttons)
		{
			if (button.update())
			{
				if (button.getText() == L"[BS]")
				{
					if (!name.isEmpty)
					{
						name.pop_back();
					}
				}
				else if (name.length < maxNameLength)
				{
					name.append(button.getText());
				}

				break;
			}
		}

		for (const auto& button : buttons)
		{
			button.draw();
		}

		RoundRect(23, 80, 594, 80, 8).draw(Color(240, 250, 255));

		FontAsset(L"Name")(name).draw(40, 90, Color(20));

		bool handCursor = false;

		for (const auto& button : buttons)
		{
			if (button.getRect().mouseOver)
			{
				handCursor = true;
				break;
			}
		}

		Cursor::SetStyle(handCursor ? CursorStyle::Hand : CursorStyle::Default);
	}
}
